=====================================
API Documentation
=====================================

Overview
========

The ZATCA Middleware provides a comprehensive set of API endpoints designed to comply with the Zakat, Tax and Customs Authority (ZATCA) regulations in Saudi Arabia. This documentation covers the various endpoints available for managing companies, locations, compliance, reporting, and clearance processes.

Postman API collection
=====================
It is also available as a Postman collection for a better understanding of the payload, authentication, and response. You can access it here: `Postman Collection <https://documenter.getpostman.com/view/38384740/2sAXqtbgdG>`_.



Authentication
==============

To interact with the API, you must authenticate by obtaining a token.

.. code-block:: http

    POST /api/token/

    Request Body:
    {
        "username": "admin",
        "password": "admin"
    }

    Response:
    {
        "access": "your-access-token",
        "refresh": "your-refresh-token"
    }

Company Management
==================

These endpoints allow you to manage companies within the middleware.

.. code-block:: http

    POST /api/company/

    Request Body:
    {
        "name": "ERP Technology"
    }

    Response: 201 Created

.. code-block:: http

    GET /api/company/{slug}/

    Response:
    {
        "name": "ERP Technology",
        "slug": "erp-technology",
        "id": "72ac562a-9288-4020-87c8-0193f0244679"
    }

.. code-block:: http

    PUT /api/company/{slug}/

    Request Body:
    {
        "name": "erp-technology"
    }

    Response: 200 OK

.. code-block:: http

    PATCH /api/company/{slug}/

    Request Body:
    {
        "name": "ERP Technology LLC"
    }

    Response: 200 OK

.. code-block:: http

    DELETE /api/company/{slug}/

    Response: 204 No Content

Location Management
===================

Manage locations for companies through these endpoints.

.. code-block:: http

    POST /api/locations/

    Request Body:
    {
        "seller_name": "ERP age technology",
        "tax_no": "300811121100003",
        "organisation": "Jeddah Branch",
        "serial_number": "1-einvotca.com|2-version 2.0|3-ed22f1d8-e6a2-1118-9b58-d9a8f11e445f",
        "organisation_unit": "Jeddah Branch",
        "registered_address": "National Address",
        "business_category": "Informational Technology",
        "title": "1100",
        "common_name": "ERP age technology"
    }

    Response: 201 Created

Sandbox Environment
====================

These endpoints allow you to test compliance, clearance, and reporting processes in a sandbox environment.

**Generate CSID**

.. code-block:: http

    GET /api/sandbox/csid/

    Response:
    {
        "csid": "Generated CSID"
    }

**Compliance - Standard Invoice**

.. code-block:: http

    POST /api/sandbox/compliance/invoice/

    Request Body:
    {
        "invoice": {
            "invoiceType": "standard",
            "documentType": "invoice"
        },
        ...
    }

    Response: 200 OK

**Compliance - Simplified Invoice**

.. code-block:: http

    POST /api/sandbox/compliance/invoice/

    Request Body:
    {
        "invoice": {
            "invoiceType": "simplified",
            "documentType": "invoice"
        },
        ...
    }

    Response: 200 OK

**Generate X.509**

.. code-block:: http

    PATCH /api/sandbox/x509/

    Response:
    {
        "x509": "Generated X.509 Certificate"
    }

Production Environment
=======================

These endpoints manage the clearance, compliance, and reporting processes for production.

**Clearance - Standard Invoice**

.. code-block:: http

    POST /api/production/clearance/

    Request Body:
    {
        "invoice": {
            "invoiceType": "standard",
            "documentType": "invoice"
        },
        ...
    }

    Response: 200 OK

**Compliance - Standard Invoice**

.. code-block:: http

    POST /api/production/compliance/invoice/

    Request Body:
    {
        "invoice": {
            "invoiceType": "standard",
            "documentType": "invoice"
        },
        ...
    }

    Response: 200 OK

**Reporting**

.. code-block:: http

    POST /api/production/reporting/

    Request Body:
    {
        "invoice": {
            "invoiceType": "simplified",
            "documentType": "invoice"
        },
        ...
    }

    Response: 200 OK

Conclusion
==========

This documentation provides an overview of the key API endpoints available in the ZATCA Middleware. For full details on request and response formats, refer to the API reference or contact support.
