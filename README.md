# Academy Manager Backend

Backend API for Academy Manager application built with Express.js.

## 🌐 Production

**API Base URL:** https://academy-manager-back.vercel.app

### Live Endpoints

Try these endpoints to see the data:

- **Students:** https://academy-manager-back.vercel.app/api/students
- **Courses:** https://academy-manager-back.vercel.app/api/courses
- **Users:** https://academy-manager-back.vercel.app/api/users

## 🚀 Local Development

1. Install dependencies:

```bash
npm install
```

2. Start the server:

```bash
npm start
```

The API will be available at `http://localhost:3000`

## 📡 API Endpoints

All endpoints are prefixed with `/api`:

### Users

- `GET /api/users` - Get all users
- `GET /api/users/:id` - Get user by ID
- `POST /api/users` - Create new user
- `PUT /api/users/:id` - Update user
- `DELETE /api/users/:id` - Delete user

### Courses

- `GET /api/courses` - Get all courses
- `GET /api/courses/:id` - Get course by ID
- `POST /api/courses` - Create new course
- `PUT /api/courses/:id` - Update course
- `DELETE /api/courses/:id` - Delete course

### Students

- `GET /api/students` - Get all students
- `GET /api/students/:id` - Get student by ID
- `POST /api/students` - Create new student
- `PUT /api/students/:id` - Update student
- `DELETE /api/students/:id` - Delete student

## 🌐 Deploy to Vercel

1. Install Vercel CLI:

```bash
npm install -g vercel
```

2. Deploy:

```bash
vercel
```

3. For production deployment:

```bash
vercel --prod
```

## ⚠️ Important Notes

- Data is stored in memory and will reset on each deployment
- CORS is enabled for all origins
- Perfect for demos and academic projects
