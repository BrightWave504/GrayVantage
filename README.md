# GrayVantage Academic & Corporate Services — front-end prototype

## GitHub Pages
Upload `index.html` and the entire `assets/` folder to the root of your repository. Go to **Settings → Pages → Deploy from a branch → main / (root)**.

## Included
- Public landing page and program details
- Application form with local demo storage
- Approval/rejection and examination scheduling in local demo admin mode
- Generated usernames: first two letters of first name + last name + exam month number, uppercase (e.g. JODIWA12)
- Examinee dashboard with Zoom link and scheduled exam access
- IT demo dashboard with user directory

## Important production requirements
This is NOT an authentication or exam-security system. Demo records are saved in the browser's localStorage and do not sync between users/devices. Demo admin/IT modes are not protected. Do not collect real applicant data using this prototype.

For production, use Supabase Auth with **random one-time activation/reset passwords**, not date-of-birth passwords. Generate usernames and approve applications in trusted Supabase Edge Functions; store account roles in a protected database table; enforce RLS; use private file storage; log admin actions; and verify examination opening times server-side. Static JavaScript controls alone cannot secure exam access. Do not store or show plaintext passwords or expose service-role keys in GitHub Pages.

Recommended Supabase tables: `applications`, `profiles`, `exam_sessions`, `exam_access`, `audit_logs`. Create a protected admin invitation/bootstrap process before enabling production admin accounts. Include consent, retention and privacy notices for applicant information.

## Updated CPOA application
The form now has only email, full name, school/campus, course/program, DOB, CPOA program, examination batch/month, privacy consent and submit. GCash and GoTyme QR images are included. The program information and November 7, 2026 timetable are shown as provided; update dates for later batches.

**Email workflow is not yet operational:** To automatically email applicants after submission, integrate Supabase with a trusted server-side email service (e.g. Resend) and send an email requesting proof of payment and a school or government ID. Do not place email service secrets in `index.html`. Admin verification and account provisioning must be server-side.
