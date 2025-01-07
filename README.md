# IMS
Inventory Management System

Keeping track of household items, their condition, purchase dates, and maintenance schedules can be challenging. This platform will help users catalog their home inventory, including valuable items, furniture, appliances, and more by creating and attaching barcodes to the items, and then reading with their phone cameras to capture the barcode of the product using apis like ZXing. Users will be able to set reminders for maintenance or replacement needs, and visualize their inventory through charts or dashboards. Data will include item descriptions, purchase details if any, maintenance records,  user-generated notes, and the location of the item in the house manually, or in the world with an api like google maps api with dropped pings or something like that.


## **Database Schema**
1. **Users** Table:
    
    - `id` (Primary Key)
    - `username` (Unique)
    - `email` (Unique)
    - `password_hash` (Encrypted)
    - `email`(yeah)
2. **Items** Table:
    
    - `id` (Primary Key)
    - `user_id` (Foreign Key to Users)
    - `name` (Text)
    - `category` (Text)
    - `description` (Text)
    - `value` (Numeric)
    - `purchase_date` (Date)
    - `location` (Text)
    - `barcode` (Text, Unique)
3. **Reminders** Table (maybe):
    
    - `id` (Primary Key)
    - `item_id` (Foreign Key to Items)
    - `reminder_date` (Date)
    - `message` (Text)
4. **Barcode Logs** Table:
    
    - `id` (Primary Key)
    - `item_id` (Foreign Key to Items)
    - `scan_date` (Timestamp)
    - `action` (Text, e.g., "Checked In", "Checked Out")

### **Stack Focus**

**Full-Stack Application**:  
The project will have an even focus on both the front-end and back-end. The front-end will provide an interface for cataloging and managing inventory, while the back-end will handle data storage, barcode generation, and API integrations.

---

### **Type**

**Website**:  
The app will be a web application accessible from desktop.

---

### **Goal**

The goal is to help users manage their home inventory by cataloging items, tracking valuables, generating and scanning barcodes, and receiving maintenance or replacement reminders. The platform will make home organization easier.

---

### **Users**

The primary users are **homeowners, renters, and property managers** who want to keep an organized record of their possessions.  users may include small business owners who want a simple solution for inventory management.

---

### **Data**

- **Data to Be Used**:
    
    - Item details: Name, category, description, value, purchase date, location, and warranty/maintenance information.
    - Barcode data: Generated and scanned barcodes for quick item lookup.
    - User account data: To enable personalization and secure access to inventory.
- **Data Collection**:
    
    - Users will manually input item details or upload receipts, warranties, or images.
    - Barcodes will be generated for cataloged items using the **Online Barcode Generator API** or similar service.
    - Barcode decoding will be implemented using the **ZXing API** or "allowing users to scan existing barcodes for data retrieval or product verification" not sure yet of that last part
- **Additional Sources**:
    
    - If integrating product lookup features, data will be fetched from APIs like **Barcode Lookup API** to retrieve product details based on the bardcodes.
    - The database will be managed with **PostgreSQL** and preloaded with common household item categories for ease of use, like electro domestics, .
    - Also maybe could add OpenCage geocoder API and Leaflet.js to create an interactive map, though I'll need to see if I can pull it off

## **Database Schema**

Here’s a possible schema design for PostgreSQL:

1. **Users** Table:
    
    - `id` (Primary Key)
    - `username` (Unique)
    - `email` (Unique)
    - `password_hash` (Encrypted)
2. **Items** Table:
    
    - `id` (Primary Key)
    - `user_id` (Foreign Key to Users)
    - `name` (Text)
    - `category` (Text)
    - `description` (Text)
    - `value` (Numeric)
    - `purchase_date` (Date)
    - `location` (Text)
    - `barcode` (Text, Unique)
3. **Reminders** Table (maybe):
    
    - `id` (Primary Key)
    - `item_id` (Foreign Key to Items)
    - `reminder_date` (Date)
    - `message` (Text)
4. **Barcode Logs** Table:
    
    - `id` (Primary Key)
    - `item_id` (Foreign Key to Items)
    - `scan_date` (Timestamp)
    - `action` (Text, e.g., "Checked In", "Checked Out")

---

### **API Issues**

1. **Data Quality**:
    
    - If using APIs like Barcode Lookup, the product details might be incomplete or inconsistent. To handle this, I'll allow users to manually edit fetched data.
2. **Rate Limits**:
    
    - Free tiers of APIs often impose limits on requests. which could make testing a bit hard 

---

### **Sensitive Information to Secure**

1. **User Credentials**:
    
    - Use a password hashing algorithm like bcrypt.
    - Ensure the app supports HTTPS to encrypt data during transmission.
2. **API Keys**:
    
    - Store API keys for Barcode Lookup securely in environment variables.
3. **Personal Data**:
    
    - Protect user data like inventory details and email addresses with database encryption

---

### **Functionality**

1. **Core Features**:
    
    - User registration and authentication.
    - Inventory management: Add, update, delete, and view items.
    - Barcode generation and scanning for items.
    - Maintenance reminders and notifications.
    - Integration with external APIs to fetch product details.
    - Activity logs for barcode scanning history.

---

### **User Flow**

1. **Sign-Up/Login**:
    
    - Users create an account or log in.
2. **Dashboard**:
    
    - View an overview of inventory, reminders, and recent activity.
3. **Add Item**:
    
    - Manually enter item details or scan a barcode to fetch details from an API.
    - Optionally generate a barcode for the item.
4. **Manage Items**:
    
    - View, edit, or delete items in the inventory.
5. **Scan Barcode**:
    
    - Scan an item’s barcode to mark it as “Checked In” or “Checked Out” and log the action.
6. **Reminders**(maybe):
    
    - Set up notifications for warranties or maintenance.

---

### **Features Beyond CRUD**

1. **Barcode Integration**:
    
    - The ability to generate and scan barcodes makes it more than a standard CRUD app.
2. **API Integration**:
    
    - Fetching data from external APIs adds dynamic, real-time functionality.
3. **Reminders and Notifications**:
    
    - Users receive alerts for warranty expiration or maintenance schedules.
4. **Activity Logs**:
    
    - Track the history of barcode scans and item interactions.

---

### **Stretch Goals**

1. Reminder functionality
2. location with google maps
