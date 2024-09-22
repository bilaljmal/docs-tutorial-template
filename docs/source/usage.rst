Important Instruction
==========================

**Swagger Documentation Access**
-------------------------------------

The Swagger documentation can be accessed at the following endpoint:

- **Swagger UI**: `/swagger/`

API Headers
-----------

1. **Authentication Endpoint**
   - The authentication endpoint is used to obtain a token.
   - This token is required for subsequent API calls to manage company details.

### Authentication Endpoint Response
--------------------------------------

Upon successful authentication, the endpoint returns the following JSON response:

.. code-block:: json

    {
        "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTcyNzA4OTMzMSwiaWF0IjoxNzI3MDAyOTMxLCJqdGkiOiI4MmNiZGJlZmY0MWU0ZWZiYjQzODg0N2E1NGI4ZjljMSIsInVzZXJfaWQiOjF9.vhzfuV29qtGGvHzT29cwyr-kqYL-NYvoVIwsXlHFb5A",
        "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNzI3MDAzMjMxLCJpYXQiOjE3MjcwMDI5MzEsImp0aSI6IjdmODNjNThiZTg4OTQ5MTZiNTYxZjg2ODI1NmFlZjYwIiwidXNlcl9pZCI6MX0.NYQaGUxk_N2bD0dE9mqs6Thw2DgSQ4M0FQgbCt1Ixpc"
    }

### Fields

- **refresh**: A token used to obtain a new access token when the current one expires.
- **access**: The access token used for authorizing subsequent API requests.

2. **Company Management**

### Company Creation Endpoint Response
----------------------------------------

Upon successfully creating a company, the endpoint returns the following JSON response:

.. code-block:: json

    {
        "name": "erp technology",
        "slug": "ae945d0b-217d-4f51-a45c-9407edbd30c3",
        "api_key": "Its51xK0.gbbY6BMuVZmDxVyezQSSSOAnDRVeDanZ"
    }

### Fields

- **name**: The name of the company.
- **slug**: A unique identifier used for updating the company details.
- **api_key**: A key required for creating EGS locations related to the company.

3. **EGS Location Management**

### Location Creation Payload
--------------------------------

The payload for creating a location requires the following JSON structure:

.. code-block:: json

    {
        "seller_name": "Erp technology",
        "tax_no": "300111111100003",
        "organisation": "Jeddah Branch",
        "serial_number": "1-einvotca.com|2-version 2.0|3-ed22f1d8-e6a2-1118-9b58-d9a8f11e445f",
        "organisation_unit": "Jeddah Branch",
        "registered_address": "Street, Jeddah",
        "business_category": "Informational Technology",
        "title": "1100",
        "common_name": "Erp technology"
    }

### Fields

- **seller_name**: The name of the seller associated with the location.
- **tax_no**: The tax identification number for the location.
- **organisation**: The name of the organization associated with the location.
- **serial_number**: A serialized string containing three components, separated by '|':
    1. **Provider Name**: The name of the provider (e.g., `einvotca.com`).
    2. **Version or Number**: The version of the service (e.g., `version 2.0`).
    3. **UUID**: A unique identifier (e.g., `ed22f1d8-e6a2-1118-9b58-d9a8f11e445f`).
- **organisation_unit**: The specific unit within the organization.
- **registered_address**: The registered address of the location.
- **business_category**: The category of business for the location.
- **title**: The type of invoice to submit, where:
    - `1000`: B2B (Business to Business)
    - `0100`: B2C (Business to Consumer)
    - `1100`: Both B2B and B2C
- **common_name**: A common name for the location.

### Location Creation Endpoint Response
-----------------------------------------

Upon successfully creating a location, the endpoint returns the following JSON response:

.. code-block:: json

    {
        "id": 6,
        "secret": "ad5b0075058a55fdb1f90677e50faeb95c224ecda24f5b2e8d00291578e0d3e9",
        "seller_name": "Erp technology",
        "tax_no": "300111111100003",
        "common_name": "Erp technology",
        "organisation": "Jeddah Branch",
        "organisation_unit": "Jeddah Branch",
        "serial_number": "1-einvotca.com|2-version 2.0|3-ed22f1d8-e6a2-1118-9b58-d9a8f11e445f",
        "title": "1100",
        "registered_address": "Street, Jeddah",
        "business_category": "Informational Technology"
    }

### Fields

- **id**: A unique identifier for the created location.
- **secret**: A key used for making invoices API calls.
- **seller_name**: The name of the seller associated with the location.
- **tax_no**: The tax identification number for the location.
- **common_name**: A common name for the location.
- **organisation**: The name of the organization associated with the location.
- **organisation_unit**: The specific unit within the organization.
- **serial_number**: A serialized string containing three components, separated by '|':
    1. **Provider Name**: The name of the provider (e.g., `einvotca.com`).
    2. **Version or Number**: The version of the service (e.g., `version 2.0`).
    3. **UUID**: A unique identifier (e.g., `ed22f1d8-e6a2-1118-9b58-d9a8f11e445f`).
- **title**: The type of invoice to submit, where:
    - `1000`: B2B (Business to Business)
    - `0100`: B2C (Business to Consumer)
    - `1100`: Both B2B and B2C
- **registered_address**: The registered address of the location.
- **business_category**: The category of business for the location.

