# Article Intake — Deployment Guide

## Overview
This guide provides instructions for deploying the Article Intake application, which consists of a React frontend and Node.js backend with OpenAI Vision API integration.

## Prerequisites
- Node.js 18+ and pnpm
- OpenAI API key
- Web server or cloud platform

## Local Development

### 1. Install Dependencies
```bash
pnpm install
```

### 2. Build the Application
```bash
pnpm run build
```

### 3. Start the Server
```bash
pnpm run server
```

The application will be available at http://localhost:3001

## Production Deployment

### Option 1: Node.js Server (Recommended)

1. **Prepare the environment:**
   ```bash
   # Install Node.js and pnpm on your server
   curl -fsSL https://get.pnpm.io/install.sh | sh
   ```

2. **Deploy the application:**
   ```bash
   # Copy all files to your server
   # Install dependencies
   pnpm install --prod
   
   # Build the application
   pnpm run build
   
   # Start the server
   pnpm run start
   ```

3. **Environment Variables:**
   ```bash
   export OPENAI_API_KEY=your_openai_api_key_here
   export PORT=3001
   export NODE_ENV=production
   ```

### Option 2: Static Hosting + Serverless Functions

1. **Deploy Frontend:**
   - Build the application: `pnpm run build`
   - Upload the `dist/` folder to your static hosting service (Netlify, Vercel, etc.)

2. **Deploy Backend:**
   - Deploy `server.js` as a serverless function
   - Configure environment variables for OpenAI API key

### Option 3: Docker Deployment

1. **Create Dockerfile:**
   ```dockerfile
   FROM node:18-alpine
   WORKDIR /app
   COPY package*.json ./
   RUN npm install --production
   COPY . .
   RUN npm run build
   EXPOSE 3001
   CMD ["npm", "run", "server"]
   ```

2. **Build and run:**
   ```bash
   docker build -t article-intake .
   docker run -p 3001:3001 -e OPENAI_API_KEY=your_key article-intake
   ```

## Configuration

### Environment Variables
- `OPENAI_API_KEY`: Your OpenAI API key
- `PORT`: Server port (default: 3001)
- `NODE_ENV`: Environment (development/production)

### Application Settings
- **Mapping API URL**: Configure in advanced settings (default: http://localhost:3001)
- **Strict JSON**: Enable/disable strict JSON parsing from OpenAI
- **Mock Mode**: Test without API calls

## API Endpoints

### POST /api/extract
Extract garment attributes using OpenAI Vision API.

**Request:**
```json
{
  "image": "base64_encoded_image"
}
```

**Response:**
```json
{
  "items": [{
    "index": 1,
    "attributes": { ... },
    "confidence": { ... }
  }]
}
```

### POST /api/map
Map extracted attributes to V2 database structure.

**Request:**
```json
{
  "attributes": { ... }
}
```

**Response:**
```json
{
  "v2": { ... }
}
```

## Troubleshooting

### Common Issues

1. **OpenAI API Errors:**
   - Verify API key is correct
   - Check API quota and billing
   - Ensure proper request format

2. **File Upload Issues:**
   - Check file size limits (10MB max)
   - Verify supported formats (JPEG, PNG)
   - Ensure proper CORS configuration

3. **Build Errors:**
   - Clear node_modules and reinstall
   - Check Node.js version compatibility
   - Verify all dependencies are installed

### Performance Optimization

1. **Frontend:**
   - Enable gzip compression
   - Use CDN for static assets
   - Implement lazy loading

2. **Backend:**
   - Add request rate limiting
   - Implement caching for repeated requests
   - Use connection pooling

## Security Considerations

1. **API Keys:**
   - Store securely in environment variables
   - Never commit to version control
   - Rotate regularly

2. **File Uploads:**
   - Validate file types and sizes
   - Scan for malware
   - Implement rate limiting

3. **CORS:**
   - Configure appropriate origins
   - Limit allowed methods
   - Validate headers

## Monitoring and Logging

1. **Application Logs:**
   - Monitor API response times
   - Track error rates
   - Log user interactions

2. **System Metrics:**
   - CPU and memory usage
   - Network traffic
   - Disk space

## Support

For technical support or deployment assistance, contact the development team.
