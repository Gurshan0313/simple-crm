# Simple CRM

A simple Customer Relationship Management (CRM) web application built with Ruby on Rails. This project was built as a multi-part coding challenge to practice Rails fundamentals including Active Record, routing, partials, and migrations.

## Features

- **Admin Dashboard** — Full CRUD for customers via ActiveAdmin
- **Customer Image Uploads** — Profile images stored with ActiveStorage
- **All Customers View** — Browse every customer in the system
- **Alphabetized View** — Customers sorted A–Z by full name
- **Missing Email View** — Quickly find customers with no email address on file
- **Reusable Partial** — Customer cards rendered via a shared ERB partial
- **Form Validations** — Ensures full name is always present; validates email format

## Tech Stack

- **Ruby on Rails 7.2**
- **SQLite** (development database)
- **ActiveAdmin 3.4** — admin interface
- **Devise 4.9** — admin authentication
- **ActiveStorage** — image uploads
- **Bulma CSS** — frontend styling via CDN

## Getting Started

### Prerequisites

- Ruby 3.1.2
- Rails 7.2
- Bundler

### Setup

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/simple-crm.git
cd simple-crm

# Install dependencies
bundle install

# Set up the database
rails db:create
rails db:migrate
rails db:seed

# Start the server
rails s
```

Then visit `http://localhost:3000`

## Admin Access

Visit `http://localhost:3000/admin`

| Field    | Value                 |
|----------|-----------------------|
| Email    | admin@example.com     |
| Password | password              |

> Change these credentials in production!

## Routes

| URL                        | Action          | Description                          |
|----------------------------|-----------------|--------------------------------------|
| `/`                        | index           | All customers                        |
| `/customers/alphabetized`  | alphabetized    | Customers sorted A–Z                 |
| `/customers/missing_email` | missing_email   | Customers with no email address      |
| `/admin`                   | —               | ActiveAdmin dashboard                |

## Project Structure

```
app/
├── controllers/
│   └── customers_controller.rb   # index, alphabetized, missing_email actions
├── models/
│   └── customer.rb               # Validations, ActiveStorage, Ransack config
├── views/
│   └── customers/
│       ├── _customer.html.erb    # Reusable customer card partial
│       ├── index.html.erb        # All customers
│       ├── alphabetized.html.erb # Sorted customers
│       └── missing_email.html.erb# Customers missing email
└── admin/
    └── customers.rb              # ActiveAdmin resource config
```

## Customer Model

| Field          | Type    | Notes                        |
|----------------|---------|------------------------------|
| full_name      | string  | Required                     |
| phone_number   | string  |                              |
| email_address  | string  | Optional, validated if present|
| notes          | text    |                              |
| image          | —       | ActiveStorage attachment     |

## Author

Gurshan — built as part of a Rails CRM coding challenge.