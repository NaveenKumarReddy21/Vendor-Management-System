# Vendor Management System using Django & Rest API

A Vendor Management System using Django and Django REST Framework. This system manages vendor profiles, tracks purchase orders, and calculates vendor performance metrics.

# Django REST API Setup

This repository contains a Django project with a RESTful API using Django REST Framework.


# Setup Instructions

## Install Dependencies:
- Django (latest stable version)
- Django REST Framework (latest stable version)
- Token-based authentication
- PEP 8 compliant code
- Comprehensive data validations
- Django ORM for database interactions

## installation:
##Clone Repo: (copy below git clone to cmd)
    ```bash
    git clone 
    cd C:\Users\your_user_name\

1. Create and activate a virtual environment:
    ```bash
    python -m venv venv
    .\venv\Scripts\activate

   
2. Install dependencies:
   ```bash
    pip install -r requirements.txt

3. Run migrations:
    ```bash 
    python manage.py makemigrations
    python manage.py migrate

4. Create Superuser and Token:
    ```bash
    python manage.py createsuperuser
    curl -X POST -d "username=your_superuser_username&password=your_superuser_password" http://localhost:8000/


5. Run :
    ```bash 
    python manage.py runserver


## Access Django Admin:
Open the Django admin at http://127.0.0.1:8000/admin/ and log in using the superuser credentials. this is to access the database as a admin user.

## how to run a api endpoint:
- first we need to make sure that we migrated the models to database
- then we need to start the server using "python manage.py runserver" command.
- then we need to open another cmd prompt and open virtual environment and open the project folder and provide curl or http i.e commands.

# Testing or Using the API endpoints.
- we can test API endpoints using curl or http i.e commands. 

## Create a vendor:
### using curl:
- curl -H "Authorization: Token your_obtained_token" -X POST http://127.0.0.1:8000/api/vendors/ -d "vendor_code=01&name=Vendor+1&contact_details=Contact+1&address=Address+1"
### using http i.e:
- http POST http://127.0.0.1:8000/api/vendors/ vendor_code=01 name="Vendor 1" contact_details="Contact 1" address="Address 1" "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint is used to create a vendor by providing the vendor details.

## List all Vendors details:
### using curl:
- curl -H "Authorization: Token your_obtained_token" http://127.0.0.1:8000/api/vendors/
### using http i.e:
- http http://127.0.0.1:8000/api/vendors/ "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint is used to get the details of all vendors.

## Retrieve a specific vendor's details:
### using curl:
- curl -H "Authorization: Token your_obtained_token" http://127.0.0.1:8000/api/vendors/{vendor_id}/
### using http i.e:
- http http://127.0.0.1:8000/api/vendors/{vendor_id}/ "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint is used to get the details of vendor with vendor_id which was mentioned in the command. 

## Update a vendor's details:
### using curl:
#### PUT method:
- curl -H "Authorization: Token your_obtained_token" -X PUT http://127.0.0.1:8000/api/vendors/{vendor_id}/ -d "vendor_code=updated code&name=Updated Vendor Name&contact_details=Updated Contact Details&address=Updated Address"
#### PATCH method:
- curl -H "Authorization: Token your_obtained_token" -X PATCH http://127.0.0.1:8000/api/vendors/{vendor_id}/ -d "name=Updated Vendor Name"
### using http i.e:
#### PUT method:
- http PUT http://127.0.0.1:8000/api/vendors/{vendor_id}/ vendor_code="updated vendor code" name="Updated Vendor Name" contact_details="Updated Contact Details" address="Updated Address" "Authorization: Token your_obtained_token"
#### PATCH method:
- http PATCH http://127.0.0.1:8000/api/vendors/{vendor_id}/ name="Updated Vendor Name" contact_details="Updated Contact Details" address="Updated Address" "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint we have two commands with different http methods (PUT,PATCH).As we have a primary key in the model the PUT method works as POST method (which means it creates a new vendor with given details). The PATCH method is used to update the vendor's details except vendor's id. here PUT handles updates by replacing the entire entity, so it creates a new entity. but where the PATCH handles by only updating the given fields.

## Delete a vendor:
### using curl:
- curl -H "Authorization: Token your_obtained_token" -X DELETE http://127.0.0.1:8000/api/vendors/{vendor_id}/
### using http i.e:
- http DELETE http://127.0.0.1:8000/api/vendors/{vendor_id}/ "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint is used to delete the vendor with given vendor_id.

## Create a purchase_order:
### using curl:
- curl -H "Authorization: Token your_obtained_token" -X POST http://127.0.0.1:8000/api/purchase_orders/ -d "po_number=01&vendor=01&order_date=2023-01-01T12:00:00&delivery_date=2023-01-10T12:00:00&items=[{\"item_name\":\"Item 1\",\"quantity\": 10 },{\"item_name\": 10 }]&quality_rating=4.5&issue_date=2023-01-01T12:00:00&status=updated&acknowledgment_date=2023-01-02T12:00:00"
### using http i.e:
- http POST http://127.0.0.1:8000/api/purchase_orders/ po_number="01" vendor=01 order_date="2023-01-01" delivery_date="2023-01-10" items='[{"item_name": 20 }]' quality_rating=4.5 issue_date="2023-01-01" status="Pending" acknowledgment_date="2023-01-02" "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint is used to create a purchase_order with given details.

## List all purchase_orders details:
### using curl:
- curl -H "Authorization: Token your_obtained_token" http://127.0.0.1:8000/api/purchase_orders/
### using http i.e:
- http http://127.0.0.1:8000/api/purchase_orders/ "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint is used to get the details of all purchase_orders.

## Retrieve a specific purchase_order's details:
### using curl:
- curl -H "Authorization: Token your_obtained_token" http://127.0.0.1:8000/api/purchase_orders/{po_id}/
### using http i.e:
- http http://127.0.0.1:8000/api/purchase_orders/{po_id}/ "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint is used to get the details of purchase_order with given po_id.

## Update a purchase_order's details:
### using curl:
#### PUT method:
- curl -H "Authorization: Token your_obtained_token" -X PUT http://127.0.0.1:8000/api/purchase_orders/{po_id}/ -d "po_number=updatedno&vendor=updatedvno&order_date=2023-01-02T12:00:00&delivery_date=2023-01-15T12:00:00&items=[{\"item_name\": 10 },{\"item_name\":10}]&quality_rating=5&issue_date=2023-01-01T12:00:00&status=updated&acknowledgment_date=2023-01-01T12:00:00"
#### PATCH method:
- curl -H "Authorization: Token your_obtained_token" -X PATCH http://127.0.0.1:8000/api/purchase_orders/{po_id}/ -d "vendor=updatedvno&quality_rating=5"
### using http i.e:
#### PUT method:
- http PUT http://127.0.0.1:8000/api/purchase_orders/{po_id}/ po_number="UpdatedPO001" vendor="updatedid" order_date="2023-01-02T12:00:00" delivery_date="2023-01-15T12:00:00" items:='[{"item_name": 20 }]' quality_rating:=4.8 issue_date="2023-01-01" status="updated" acknowledgment_date="2023-01-02" "Authorization: Token your_obtained_token"
#### PATCH method:
- http PATCH http://127.0.0.1:8000/api/purchase_orders/{po_id}/ order_date="2023-01-02T12:00:00" delivery_date="2023-01-15T12:00:00" items:='[{"item_name": "Updated Item", "quantity": 20 }]' quality_rating:=4.8 status="updated" "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint we have two commands with different http methods (PUT,PATCH).As we have a primary key in the model the PUT method works as POST method (which means it creates a new purchase_order with given details). The PATCH method is used to update the purchase_order's details except purchase_order's number. here PUT handles updates by replacing the entire entity, so it creates a new entity. but where the PATCH handles by only updating the given fields.(we can provide any no of fields in PATCH mathod.)

## Delete a purchase_order:
### using curl:
- curl -H "Authorization: Token your_obtained_token" -X DELETE http://127.0.0.1:8000/api/purchase_orders/{po_id}/
### using httpie:
- http DELETE http://127.0.0.1:8000/api/purchase_orders/{po_id}/ "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint is used to delete a purchase_order with given po_id.

## Retrieve a vendor's performance metrics:
### using curl:
- curl -H "Authorization: Token your_obtained_token" http://127.0.0.1:8000/api/vendors/1/performance/
### using http i.e:
- http http://127.0.0.1:8000/api/vendors/1/performance/ "Authorization: Token your_obtained_token"
### About this API endpoint:
- here this endpoint is used to retrieve the performance metrics of a vendor with given vendor_id. this performance metrics contains on_time Delivery rate, quality rating average, average response time, fulfilment rate
- On time delivery rate is calculated each time a PO status changes to "completed". this is the average of no of po delivered before the delivery_date and no of total po's delivered.
- quality rating average is calculated after every po completion and it is the average of all ratings given to that specific vendor.
- average response time is calculated each time a po is acknowledged by the vendor. it is the time difference between issue_date and acknowledgment_date for each po, and then the average of these times for all po's of the vendor.
- fulfillment rate is calculated when po status is set to "completed". this is the average of no of successfully fulfilled pos (status = "completed" without issues) by the total no of pos issued to the vendor.

## Update acknowledgment_data and trigger the recalculation of average_response_time:
### using curl:
- curl -H "Authorization: Token your_obtained_token" -X PATCH http://127.0.0.1:8000/api/purchase_orders/{po_id}/acknowledge/ --data "acknowledgment_date=2023-12-30T12:00:00Z"
### using http i.e:
- http PATCH http://127.0.0.1:8000/api/purchase_orders/{po_id}/acknowledge/ "Authorization: Token your_obtained_token" acknowledgment_date="2023-12-20T12:00:00Z"
### About this API endpoint:
- here this endpoint is used to acknowledge the purchase_order with given po_id and trigger the recalculation of average_reponse_time.

