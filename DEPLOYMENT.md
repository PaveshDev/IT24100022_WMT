# Deployment Notes

## Platforms Used

### Backend
- **Render** - Node.js/Express hosting with automatic GitHub deployments
- **MongoDB Atlas** - Cloud database (free tier)

### Frontend
- **Vercel** - Vite/React hosting with automatic deployments

## Tech Stack
- **Backend**: Node.js, Express, MongoDB
- **Frontend**: React, Vite, Axios

## Local Running
```bash
# Backend
cd backend && npm install && npm run dev     # Port 5000

# Frontend
cd frontend && npm install && npm run dev    # Port 5173
```

## Environment Variables
- Backend: `MONGO_URI`, `PORT`
- Frontend: `VITE_API_URL`

## Deployment Steps
1. Push to GitHub
2. Connect repo to Render (backend) and Vercel (frontend)
3. Set environment variables in each platform
4. Auto-deploy triggers on push to main branch
