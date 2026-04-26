🧪 Real-time Testing API


A lightweight, high-performance Python API designed for real-time test execution, management, and data portability. 
Built with FastAPI, it offers instant feedback and persistent storage without the need for complex database setups or Docker.



✨ Key Features
⚡ Real-time Execution: Run test cases with instant pass/fail results.
📂 Export/Import: Full support for JSON-based test portability.
🛡️ Persistent Storage: Automatic local JSON storage—no database required.
📱 Interactive Docs: Built-in Swagger UI for testing endpoints visually.
🚀 Zero Docker: Pure Python implementation for seamless deployment.
🌐 CORS Ready: Pre-configured for easy frontend integration.



🚀 Quick Start (20 Seconds)
Install Dependencies

Bash
pip install -r requirements.txt
Initialize Sample Data

Bash
python init_data.py
Launch the API

Bash
python app.py


🔗 Useful Endpoints
Interactive Swagger UI: http://localhost:8000/docs
List All Tests: http://localhost:8000/tests
Health Status: http://localhost:8000/health


📁 Project Structure
Plaintext
real-time-testing-api/
├── app.py              # FastAPI server & logic
├── init_data.py        # Seed script for initial tests
├── requirements.txt    # Python dependencies
├── data/               # Persistent Storage (Auto-generated)
│   └── tests.json      # Main test database
└── tests/              # Internal API tests
    └── test_api.py


    
🎮 Usage Guide
1. Create a Test
Endpoint: POST /tests

Bash
curl -X POST "http://localhost:8000/tests" \
-H "Content-Type: application/json" \
-d '{
  "name": "Auth Flow",
  "cases": [{"name": "Valid Login", "input_key": "user", "expected": true}]
}'


2. Run a Test Case
Endpoint: POST /tests/{test_id}/run

Bash
curl -X POST "http://localhost:8000/tests/YOUR_ID/run" \
-H "Content-Type: application/json" \
-d '{"user": "admin_account"}'


3. Export/Import
Export: GET /export/{test_id} — Downloads the test as a .json file.
Import: POST /import — Upload a .json file to restore a test.


☁️ Deployment (No Docker)
Option 1: Render / Railway (Recommended)
Connect your GitHub repository.

Build Command: pip install -r requirements.txt
Start Command: uvicorn app:app --host 0.0.0.0 --port $PORT

Option 2: Local Server
Simply run the Python script on any machine with Python 3.8+:

Bash
python app.py


🛠️ Maintenance
Reset Data: Delete the data/tests.json file or re-run python init_data.py.
Verify Health: Monitor http://localhost:8000/health for uptime tracking.
