# StaffSync - Modern Human Resource Management (MERN)

Roles: **HR**, **Manager**, **Employee** (JWT auth, role-based access).

| Role | Can do |
|------|--------|
| HR | Add/edit/delete employees, approve/reject any leave, view all attendance, post announcements, create training |
| Manager | View own team, approve/reject team leaves, view team attendance, create training for team |
| Employee | Apply/cancel leave, check in/out, edit profile, read announcements, view assigned training |

## Quick start (Windows)

Needs: Node.js 18+ and MongoDB running on `localhost:27017`.

Open Command Prompt **inside the `staffsync` folder** (the one containing `server`, `client` and this README):

```bash
npm run setup     # installs everything (once)
npm run dev       # starts backend (5000) and frontend (5173) together
```

Open http://localhost:5173 and click a demo button on the login page.

Demo accounts are created automatically every time the server starts, so the logins always work:
- HR: `hr@staffsync.com` / `Hr@12345`
- Manager: `manager@staffsync.com` / `Manager@123`
- Employee: `employee@staffsync.com` / `Employee@123`

(To run separately: `cd server && npm install && npm run dev`, and `cd client && npm install && npm run dev`.)

## Folder structure
```
server/  config/{db.js,seedDemo.js}  models/  middleware/auth.js  routes/  server.js
client/  src/{api.js, AuthContext.jsx, App.jsx, styles.css, components/, pages/}
```

## API
- `POST /api/auth/login`, `GET /api/auth/me`
- `/api/users` (HR) | `/api/leaves` | `/api/attendance` | `/api/announcements` | `/api/training`

## Deploy (for the demo link)
1. **Database:** free MongoDB Atlas cluster, copy the connection string.
2. **Backend (Render):** root dir `server`, build `npm install`, start `npm start`. Env vars: `MONGO_URI`, `JWT_SECRET` (long random text), `CLIENT_URL` (your Vercel URL). Keep `SEED_DEMO=true` for a demo (it creates the demo logins), or `false` for real use.
3. **Frontend (Vercel):** root dir `client`, framework Vite. Env var: `VITE_API_URL=https://<your-render-app>.onrender.com/api`.

## Push to GitHub
```bash
git init
git add .
git commit -m "StaffSync MERN HR management system"
git branch -M main
git remote add origin https://github.com/<your-username>/staffsync.git
git push -u origin main
```
