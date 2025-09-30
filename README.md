# Document-Management-System
Frontend Code of DMS

OTP-based login and document workflows built with React, JavaScript, and Bootstrap. Includes Registration, Admin login, Dashboard, Upload, Search, and mock API support.

## Features
- OTP Login flow (Admin/User roles)
  - Admin: username + password + OTP
  - User: mobile + OTP
  - Token persisted to localStorage
- Registration with OTP verification
- Dashboard with quick actions: Upload, Search
- Upload
  - Date picker
  - Category: Personal/Professional (major_head)
  - Dynamic secondary: Names (Personal) or Departments (Professional) (minor_head)
  - Tag input with suggestions + new tag creation
  - Remarks
  - File restrictions: PDF and images
- Search
  - Filters: Category, Tags, From/To dates
  - Results table with Preview/Download actions
  - “Download All (ZIP)” simulated
- Admin
  - Static interface to create a user (mocked)
- Dark theme with Bootstrap styling

## Tech Stack
- React (Vite)
- JavaScript
- Bootstrap 5
- React Router
- Axios

## Project Structure

src/
  api/
    auth.js            # OTP generate/validate (mock toggle)
    documents.js       # tags, upload, search (mock toggle)
  components/
    TagInput.jsx       # tag chips + suggestions
  pages/
    App.jsx            # home
    Login.jsx          # Admin/User auth (OTP)
    Register.jsx       # sign up with OTP
    Dashboard.jsx      # Upload & Search entry
    Upload.jsx         # file upload form
    Search.jsx         # filters + results
    AdminUser.jsx      # static admin create user
  main.jsx             # router
  index.css            # dark theme


## API Endpoints (from Postman)
- Generate OTP: POST `https://apis.allsoft.co/api/documentManagement/generateOTP`
  - body: `{ "mobile_number": "XXXXXXXXXX" }`
- Validate OTP: POST `https://apis.allsoft.co/api/documentManagement/validateOTP`
  - body: `{ "mobile_number": "XXXXXXXXXX", "otp": "XXXXXX" }`
- Upload: POST `.../saveDocumentEntry` (multipart/form-data)
- Search: POST `.../searchDocumentEntry`
- Tags: POST `.../documentTags`

## Mock Mode vs Real Backend
- Mock is ON by default for fast local testing. OTP is shown as Test OTP: 123456.
- To use real APIs, set `MOCK_MODE = false` in:
  - src/api/auth.js
  - src/api/documents.js

## Getting Started

### Prerequisites
- Node.js 18+

### Install

npm install


### Run (dev)

npm run dev

- Open the printed Local URL (e.g., http://localhost:5173 or 5174/5175).
- Login:
  - Choose “User” or “Admin”
  - Admin: provide username & password before OTP
  - Enter a 10-digit mobile number
  - Use OTP `123456` in mock mode
- After login you are redirected to `/dashboard`.

### Build (prod)

npm run build
npm run preview


## Usage Guide
- Home
  - Login or Register
- Login
  - Pick Admin/User, proceed with OTP verification
- Dashboard
  - Upload: Fill date, category, dynamic name/department, tags, remarks, and select a PDF or image → Upload
  - Search: Filter by category/tags/dates → Preview/Download (simulated in mock)
- Admin
  - Create user (static mock UI)

## Environment/Config
- Auth header: requests automatically include `token` from `localStorage` if present
- Token key: `dms_token`
- Role key: `dms_role` (`Admin` or `User`)

## Screenshots (optional)
Add screenshots of:
- Home, Login (Admin/User), Dashboard
- Upload form, Search results

## Git/GitHub Instructions
Initialize and push:

git init
git add .
git commit -m "feat: DMS with OTP login, upload, search, admin, mock API"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
