import frappe

# ----------------------------
# 🔹 CREATE
# ----------------------------
# Create a new ToDo document
doc = frappe.get_doc({
    "doctype": "ToDo",
    "description": "Buy groceries",
    "date": "2025-04-10"
})
doc.insert()
print(f"Created ToDo: {doc.name}")

# ----------------------------
# 🔹 READ
# ----------------------------

# Read a document by name
doc = frappe.get_doc("ToDo", doc.name)
print("Read ToDo by name:")
print(f"Description: {doc.description}, Date: {doc.date}")

# Read multiple documents with filters
todos = frappe.get_all(
    "ToDo",
    fields=["name", "description"],
    filters={"owner": frappe.session.user}
)
print("All ToDos for current user:")
for todo in todos:
    print(todo)

# Read a single field value
description = frappe.db.get_value("ToDo", doc.name, "description")
print(f"Fetched single field value: {description}")

# ----------------------------
# 🔹 UPDATE
# ----------------------------
# Update the document
doc.description = "Buy milk and eggs"
doc.date = "2025-04-11"
doc.save()
print("Updated ToDo:")
print(f"New Description: {doc.description}, New Date: {doc.date}")

# ----------------------------
# 🔹 DELETE
# ----------------------------
# Delete the document
frappe.delete_doc("ToDo", doc.name)
print(f"Deleted ToDo: {doc.name}")
