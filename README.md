# Article Intake — Vision + Mapping

A comprehensive single-page web application for garment attribute extraction using OpenAI Vision API, with field mapping, editable grid interface, and XLSX export functionality.

## Features

### Core Functionality
- **Multi-image Upload**: Upload 1-10 garment images (JPEG/PNG)
- **OpenAI Vision Integration**: Extract garment attributes using GPT-4 Vision
- **Field Mapping**: Transform extracted attributes to V2 database structure
- **Editable Grid**: Inline editing of all extracted attributes
- **Confidence Indicators**: Visual confidence scores for each attribute
- **XLSX Export**: Dual-sheet export (ART10_Generic + SKU_Variant)

### User Interface
- **Professional Design**: Modern, responsive interface with Tailwind CSS
- **Advanced Settings**: Configurable API endpoints and options
- **Mock Mode**: Test functionality without OpenAI API key
- **Image Lightbox**: Click to view full-size images
- **Real-time Updates**: Live status updates during processing

### Technical Features
- **React Frontend**: Built with modern React and TypeScript
- **Express Backend**: Node.js server with OpenAI API integration
- **Error Handling**: Comprehensive error handling and retry functionality
- **Local Storage**: Persistent API key storage
- **Responsive Design**: Works on desktop and mobile devices

## Installation

### Prerequisites
- Node.js 18+ and pnpm
- OpenAI API key (for production mode)

### Setup
1. Clone or download the project
2. Install dependencies:
   ```bash
   pnpm install
   ```

3. Build the application:
   ```bash
   pnpm run build
   ```

4. Start the server:
   ```bash
   pnpm run server
   ```

5. Open http://localhost:3001 in your browser

## Usage

### Getting Started
1. **Set Mode**: Choose between "Server Vision (OpenAI)" or "Mock" mode
2. **API Key**: Enter your OpenAI API key (for server mode)
3. **Upload Images**: Select 1-10 garment images
4. **Extract**: Click Extract to process images
5. **Review & Edit**: Review extracted attributes and edit as needed
6. **Export**: Export approved items to XLSX

### Field Mapping
The application extracts and maps the following attributes:

**Basic Information**
- Segment, Division, Sub Division
- Major Category, Season, Brand, Gender

**Fabric & Construction**
- Fabric Type, Composition, GSM, Finish
- Neck, Sleeve, Fit, Pocket, Rib, Branding

**Color & Design**
- Color Name, Color Code, Shade, Print

**Business Information**
- Sizes, Vendor, Cost, MOQ, Status
- MC Code, ART10, ART12

### Export Format
The XLSX export includes two sheets:
- **ART10_Generic**: One row per article with all V2 fields
- **SKU_Variant**: Exploded view with one row per size variant

## API Endpoints

### POST /api/extract
Extract attributes from garment image using OpenAI Vision.

**Headers:**
- `Authorization: Bearer <OPENAI_API_KEY>`
- `Content-Type: application/json`

**Body:**
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

**Body:**
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

## Configuration

### Advanced Settings
- **Mapping API URL**: Custom endpoint for field mapping
- **Strict JSON**: Enable strict JSON parsing from OpenAI
- **Mock Mode**: Test without API calls

### Environment Variables
- `OPENAI_API_KEY`: Default OpenAI API key
- `PORT`: Server port (default: 3001)

## Development

### Scripts
- `pnpm run dev`: Start development server
- `pnpm run build`: Build for production
- `pnpm run server`: Start production server
- `pnpm run start`: Build and start production server

### Project Structure
```
├── src/
│   ├── App.jsx          # Main React component
│   ├── App.css          # Styles and Tailwind imports
│   └── components/ui/   # Reusable UI components
├── server.js            # Express server with API endpoints
├── dist/                # Built frontend files
└── package.json         # Dependencies and scripts
```

## Error Handling

The application includes comprehensive error handling:
- **Network Errors**: Automatic retry for failed extractions
- **API Errors**: Clear error messages for API issues
- **Validation**: Input validation and file type checking
- **Fallbacks**: Graceful degradation when services are unavailable

## Browser Compatibility

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## License

This project is proprietary software. All rights reserved.

## Support

For technical support or feature requests, please contact the development team.
