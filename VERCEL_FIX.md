# Vercel Deployment Fix - API Connection Issue

## Problem
Items not being created in Vercel because the frontend cannot connect to the backend API.

## Solution

### Step 1: Deploy Backend to Render (or your hosting platform)
1. Go to [render.com](https://render.com)
2. Connect your GitHub repository
3. Create a new Web Service
4. Set environment variables:
   - `MONGO_URI`: Your MongoDB Atlas connection string
   - `PORT`: 5000
   - `FRONTEND_URL`: Your Vercel URL (e.g., https://your-app.vercel.app)
5. Deploy and note your Render URL (e.g., https://your-app.onrender.com)

### Step 2: Update Frontend Environment Variables in Vercel
1. Go to your project in [vercel.com](https://vercel.com)
2. Navigate to **Settings → Environment Variables**
3. Add a new environment variable:
   - **Name**: `VITE_API_URL`
   - **Value**: `https://your-app.onrender.com/api` (replace with your Render URL)
   - **Environments**: Select "Production"
4. Click "Save"
5. Trigger a new deployment (push to main or redeploy manually)

### Step 3: Verify Backend CORS
The backend now accepts requests from:
- `http://localhost:5173` (local development)
- `http://localhost:3000` (alternative local)
- Your Vercel frontend URL (via `FRONTEND_URL` environment variable)

### Step 4: Test
1. Wait for Vercel to redeploy
2. Go to your Vercel URL
3. Try adding a new item - it should now work!

## Quick Checklist
- ✅ Backend deployed on Render with MONGO_URI set
- ✅ VITE_API_URL set in Vercel environment variables
- ✅ FRONTEND_URL set in Render (or use default wildcard)
- ✅ Vercel deployment triggered after env var change

## If Still Not Working
1. Check browser console (F12) for actual error messages
2. Verify the backend URL is correct and accessible
3. Check MongoDB Atlas IP whitelist includes Render's IP
4. Check backend logs on Render for connection errors
