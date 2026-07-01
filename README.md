# ECommerce-Order-Management-System
Console-based E-Commerce Order Management System in Python using OOP principles (Encapsulation, Inheritance, Polymorphism, Abstraction) and the Strategy design pattern. Features product categories, shopping cart, multiple payment methods, order tracking, invoices, and custom exceptions.

## 📖 Overview

The system models how an online store manages products, shopping carts, payments, and orders. A customer can browse products across categories, add them to a cart, check out using one of several payment methods, and receive a detailed invoice — all while the order's status is tracked through its lifecycle.

## ✨ Features

- Manage multiple product categories (*Electronics, Clothing, Books*) each with category-specific discount rules
- Full shopping cart functionality — add/remove items and calculate totals with discounts applied
- Support for multiple payment methods — *Credit Card, Wallet, Cash on Delivery*
- Order placement and status tracking (PLACED → SHIPPED → DELIVERED / CANCELLED)
- Automatic generation of a detailed, itemized invoice
- Graceful error handling for invalid input, out-of-stock items, and failed payments

## 🧱 OOP Concepts Demonstrated

| Concept | Where it's used |
|---|---|
| *Abstraction* | Product and PaymentProcessor are abstract base classes (abc.ABC) that cannot be instantiated directly |
| *Inheritance* | Electronics, Clothing, Book inherit from Product; CreditCardPayment, WalletPayment, CODPayment inherit from PaymentProcessor |
| *Polymorphism* | apply_discount() and process_payment() behave differently per subclass but are called uniformly, with no isinstance checks |
| *Encapsulation* | Private attributes exposed via @property getters/setters with validation (e.g. price and stock can't go negative) |
| *Design Pattern* | The PaymentProcessor hierarchy implements the *Strategy Pattern*, allowing payment behavior to be swapped at runtime |

## 📂 Project Structure


ecommerce_oop/
├── main.py                     # Console menu / entry point
├── models/
│   ├── __init__.py
│   ├── product.py              # Product (ABC), Electronics, Clothing, Book
│   ├── customer.py             # Customer
│   ├── cart.py                 # ShoppingCart
│   ├── order.py                # Order, OrderStatus (Enum)
│   └── payment.py              # PaymentProcessor (ABC) + implementations
├── services/
│   ├── invoice_generator.py    # Formats and prints itemized invoices
│   └── order_manager.py        # Orchestrates the order lifecycle
├── utils/
│   └── exceptions.py           # Custom exceptions
├── requirements.txt
└── README.md


## 🧩 Key Classes

- *Product* (Abstract) — base class for all sellable items
- *Electronics, *Clothing*, *Book** — concrete product types, each with its own discount logic
- *Customer* — holds customer info, a cart, and order history
- *ShoppingCart* — manages items and calculates totals
- *PaymentProcessor* (Abstract) — interface for all payment strategies
- *CreditCardPayment, *WalletPayment*, *CODPayment** — concrete payment strategies
- *Order* — tracks items, total, status, and the chosen payment method
- *InvoiceGenerator* — produces a detailed invoice from an order

## 🚀 Getting Started

### Prerequisites
- Python 3.9 or higher (no external dependencies — standard library only)

### Installation

bash
git clone https://github.com/<your-username>/ecommerce-oop.git
cd ecommerce-oop


### Running the App

bash
python main.py


The app launches with a pre-seeded catalog of sample products and customers, so it's ready to use immediately.

## 🖥️ Usage

Once running, the console menu lets you:

1. Browse available products by category
2. Add or remove items from your cart
3. View your cart total (discounts applied automatically)
4. Checkout and choose a payment method
5. View your generated invoice
6. Track or update order status
7. Exit the application

## 🛠️ Tech Stack

- *Language:* Python 3
- *Paradigm:* Object-Oriented Programming
- *Dependencies:* None (standard library only — abc, enum, dataclasses, etc.)

## 🔮 Possible Extensions

- Factory pattern for product creation from a catalog/config file
- Observer pattern to notify customers of order status changes
- Persist products/orders to JSON so data survives between runs
- Unit tests with pytest
