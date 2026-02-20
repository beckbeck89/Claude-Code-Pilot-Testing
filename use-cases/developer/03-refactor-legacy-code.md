# Use Case: Refactor Legacy Code

## Objective

Give the AI tool a working but poorly structured piece of code and ask it to refactor into clean, modern, maintainable code. Tests the tool's understanding of design patterns, best practices, and ability to restructure without breaking functionality.

## The Task

Refactor the following monolithic function into well-structured, modular code:

```python
def process_order(order_data):
    # validate
    if not order_data.get('customer_email'):
        print("ERROR: no email")
        return False
    if not order_data.get('items'):
        print("ERROR: no items")
        return False
    import re
    if not re.match(r'[^@]+@[^@]+\.[^@]+', order_data['customer_email']):
        print("ERROR: bad email")
        return False

    # calculate
    total = 0
    for item in order_data['items']:
        price = item['price']
        qty = item['quantity']
        if qty > 10:
            price = price * 0.9  # bulk discount
        total = total + (price * qty)

    # tax
    if order_data.get('state') == 'CA':
        tax = total * 0.0725
    elif order_data.get('state') == 'NY':
        tax = total * 0.08
    elif order_data.get('state') == 'TX':
        tax = total * 0.0625
    else:
        tax = total * 0.05
    total = total + tax

    # shipping
    if total > 100:
        shipping = 0
    elif total > 50:
        shipping = 5.99
    else:
        shipping = 9.99
    if order_data.get('expedited'):
        shipping = shipping + 15.00
    total = total + shipping

    # save to database
    import sqlite3
    conn = sqlite3.connect('orders.db')
    c = conn.cursor()
    c.execute("INSERT INTO orders VALUES (NULL, ?, ?, ?, ?, ?)",
              (order_data['customer_email'], total, tax, shipping, 'pending'))
    order_id = c.lastrowid
    for item in order_data['items']:
        c.execute("INSERT INTO order_items VALUES (NULL, ?, ?, ?, ?)",
                  (order_id, item['name'], item['price'], item['quantity']))
    conn.commit()
    conn.close()

    # send email
    import smtplib
    from email.mime.text import MIMEText
    msg = MIMEText(f"Your order #{order_id} total is ${total:.2f}")
    msg['Subject'] = 'Order Confirmation'
    msg['From'] = 'shop@example.com'
    msg['To'] = order_data['customer_email']
    try:
        server = smtplib.SMTP('localhost')
        server.send_message(msg)
        server.quit()
    except:
        print("email failed")

    print(f"Order {order_id} processed: ${total:.2f}")
    return order_id
```

## Acceptance Criteria

- [ ] Code is split into separate, focused functions or classes
- [ ] Validation, pricing, persistence, and notification are separated
- [ ] Tax rates are configurable (not hardcoded if/elif chains)
- [ ] Imports are at the top of the file
- [ ] Error handling uses exceptions, not print statements
- [ ] The refactored code is functionally equivalent to the original

## Suggested Prompt

> "Refactor this order processing function into clean, modular, well-structured code. It works but it's a mess — separate concerns, improve error handling, and make it maintainable."

## What to Observe

- Does it identify all the code smells (God function, mixed concerns, bare except, inline imports)?
- Does it apply appropriate design patterns (strategy pattern for tax, repository pattern for DB)?
- Does it go too far or not far enough in refactoring?
- Does it preserve the original behavior while improving structure?
- Does it create appropriate file structure or keep everything in one file?
- Does it add type hints, docstrings, or other improvements proactively?
