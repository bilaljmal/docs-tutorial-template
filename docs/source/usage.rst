API Workflow Documentation
==========================

1. **Authentication Endpoint**
   - The authentication endpoint is used to obtain a token.
   - This token is required for subsequent API calls to manage company details.

2. **Company Management**
   - **Creating a Company**
     - Endpoint: `POST /api/companies/`
     - Returns:
       - `slug`: A unique identifier for updating the company details.
       - `api_key`: Required for creating EGS locations related to the company.

   - **Updating a Company**
     - Endpoint: `PUT /api/companies/{slug}/`
     - Requires the `slug` obtained from the company creation response.

   - **Deleting a Company**
     - Endpoint: `DELETE /api/companies/{slug}/`
     - Requires the `slug` obtained from the company creation response.

3. **EGS Location Management**
   - **Creating EGS Locations**
     - Endpoint: `POST /api/locations/`
     - Requires the `api_key` from the company creation response.
     - Returns:
       - `location_id`: A unique identifier for the created location.
       - `secret`: Used for making invoices API calls.

4. **Certificate and Invoice Management**
   - **Creating CSID and X.509 Certificate**
     - The `location_id` obtained from the EGS location creation response is used to create CSID and X.509 certificates.

   - **Making Invoices API Calls**
     - The `secret` obtained from the EGS location creation response and the `api_key` from the company creation response are required for making invoices API calls.


