Frappe CRUD Operations
This README explains how to perform CRUD operations (Create, Read, Update, Delete) in the Frappe Framework.

📘 What is CRUD?
C - Create: Add a new record to the database

R - Read: Retrieve data from the database

U - Update: Modify existing records

D - Delete: Remove records from the database

🔹 Create
To create a new document and insert it into the database, use the following code:

python
doc = frappe.get_doc({
    "doctype": "ToDo",
    "description": "Buy groceries",
    "date": "2025-04-10"
})
doc.insert()
🔹 Read
Read a Document by Name
To retrieve a specific document by its name:

python
doc = frappe.get_doc("ToDo", "TOD0001")
Read Multiple Documents
To retrieve multiple documents with specific fields and filters:

python
todos = frappe.get_all(
    "ToDo",
    fields=["name", "description"],
    filters={"owner": frappe.session.user}
)
Read a Single Field Value
To fetch a single field value directly:

python
description = frappe.db.get_value("ToDo", "TOD0001", "description")
🔹 Update
To update an existing document:

python
doc = frappe.get_doc("ToDo", "TOD0001")
doc.description = "Buy milk and eggs"
doc.date = "2025-04-11"
doc.save()
🔹 Delete
To delete a document:

python
frappe.delete_doc("ToDo", "TOD0001")
Note: The current date is Wednesday, April 09, 2025, 4:49 PM IST. Ensure that the dates used in your examples are valid and relevant.

This updated README provides clear explanations and formatting for better readability and usability.
