# debug-battel-2
## Challenges Faced & Fixes Applied

During development, several issues were identified and resolved:

### 1. Incorrect Product API Endpoint

* Issue: Product creation requests were being sent to `/api/product`.
* Root Cause: Backend route was registered as `/api/products`.
* Fix: Updated frontend API calls from `product` to `products`.

### 2. JWT Verification Secret Mismatch

* Issue: Protected routes were failing authentication.
* Root Cause: Authentication middleware was verifying tokens using `process.env.JWT_ACCESS_SECRET` while tokens were signed using `process.env.JWT_SECRET`.
* Fix: Standardized token verification to use `process.env.JWT_SECRET`.

### 3. Wrong Token Extraction After Login

* Issue: Users appeared unauthenticated after successful login.
* Root Cause: Frontend was reading `response.data.token` while backend returned `response.data.accessToken`.
* Fix: Updated token extraction logic to use `response.data.accessToken`.

### 4. Incorrect Password Field Name

* Issue: Login requests failed even with valid credentials.
* Root Cause: Password input field used the name `pass` instead of `password`.
* Fix: Renamed the field to `password`.

### 5. Environment Variable Configuration Issues

* Issue: Application failed to load required configuration values.
* Root Cause: Incorrect dotenv setup and environment variable loading.
* Fix: Corrected dotenv configuration and verified environment variable availability.

### 6. Backend Port Configuration Mismatch

* Issue: Frontend requests were targeting the wrong backend server.
* Root Cause: Port mismatch between frontend configuration and backend server.
* Fix: Updated API configuration to use the correct backend port.

### 7. Authentication & Protected Route Debugging

* Verified JWT generation, storage, retrieval, and protected route access.
* Fixed authorization issues caused by invalid token handling.

### 8. API Route Testing & Validation

* Tested all CRUD endpoints.
* Validated request payloads and backend responses.
* Fixed route naming inconsistencies and request handling errors.
