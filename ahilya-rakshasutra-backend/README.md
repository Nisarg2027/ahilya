
```bash
cd ahilya-rakshasutra-backend
# Create a virtual environment
python -m venv .venv
source .venv/Scripts/activate  # On Windows
# Install dependencies
pip install -r requirements.txt
# Run the server
uvicorn app.main:app --reload
