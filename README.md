# AI Problem Solver Backend

Backend API for the AI Problem Solver application.

## Setup Instructions

1. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

2. **Set Environment Variables**
   ```bash
   export GEMINI_API_KEY="your_gemini_api_key_here"
   ```

3. **Run the Application**
   ```bash
   python app.py
   ```
   
   Or for development:
   ```bash
   python src/main.py
   ```

## API Endpoints

### Chat API
- **POST** `/api/chat`
  - Send chat messages to AI
  - Supports text, images, and document processing
  - Request body:
    ```json
    {
      "problem": "Your question here",
      "subject": "AI Assistant",
      "file_data": {
        "mimeType": "image/png",
        "data": "base64_encoded_data",
        "fileName": "image.png",
        "extractedText": "text from document"
      }
    }
    ```

### Translation API
- **POST** `/api/translate`
  - Translate text to different languages
  - Request body:
    ```json
    {
      "text": "Text to translate",
      "target_language": "Spanish"
    }
    ```

### Admin API
- **GET** `/api/admin/users`
  - Get user statistics for admin panel
  - Requires Firebase Admin SDK configuration

## Configuration

### Firebase Setup (Optional)
1. Download your Firebase service account key
2. Place it in the project root
3. Update the path in `src/main.py`:
   ```python
   firebase_admin.initialize_app(credentials.Certificate('path/to/serviceAccountKey.json'))
   ```

### API Key Setup
Set your Gemini API key as an environment variable:
```bash
export GEMINI_API_KEY="your_api_key_here"
```

Or modify the `GEMINI_API_KEY` variable in `src/routes/ai_api.py`.

## File Structure

```
├── app.py                 # Main application entry point
├── requirements.txt       # Python dependencies
├── README.md             # This file
└── src/
    ├── main.py           # Flask application setup
    ├── models/           # Database models
    └── routes/
        ├── user.py       # User-related routes
        └── ai_api.py     # AI API routes
```

## Deployment

1. Ensure all dependencies are in `requirements.txt`
2. Set the `GEMINI_API_KEY` environment variable
3. Configure Firebase Admin SDK if using admin features
4. Deploy to your preferred hosting platform

## Notes

- The API key is intentionally left empty for security
- Add your own Gemini API key before deployment
- Firebase Admin SDK is optional but required for admin panel features
- CORS is enabled for all origins for development purposes

