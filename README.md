# ByteBusters Web 

Use Here: [ByteBusters](https://aditya-138-12.github.io/bytebusters/)

## Save all the images in a folder Named "images".

Ensure that all images used in the project are stored in a directory named `images`.

## Setting Up the Server on PythonAnywhere

1. **Set Up a PythonAnywhere Account:**
   - Go to [PythonAnywhere](https://www.pythonanywhere.com) and sign up for a free account.

2. **Upload Your Code:**
   - Go to the "Files" tab and upload your project files, including the `images` folder and your Python scripts.

3. **Set Up a Virtual Environment:**
   - Open a Bash console on PythonAnywhere.
   - Navigate to your project directory.
   - Create and activate a virtual environment:
     ```bash
     python3.7 -m venv venv
     source venv/bin/activate
     ```

4. **Install Dependencies:**
   - Install the necessary dependencies including `groq-python-sdk`:
     ```bash
     pip install -r requirements.txt
     pip install groq-python-sdk
     ```

5. **Configure Your Web App:**
   - Go to the "Web" tab and add a new web app.
   - Choose `Manual configuration` and select `Flask` for the framework.
   - Set the `WSGI configuration file` to point to your Flask app's entry point.

   Example WSGI Configuration:
   ```python
   import sys
   import os

   # Add your project directory to the sys.path
   project_home = '/home/yourusername/bytebusters'
   if project_home not in sys.path:
       sys.path = [project_home] + sys.path

   # Activate your virtual environment
   activate_this = os.path.expanduser('/home/yourusername/bytebusters/venv/bin/activate_this.py')
   with open(activate_this) as file_:
       exec(file_.read(), dict(__file__=activate_this))

   # Import your Flask app
   from app import app as application  # Change 'app' to your Flask app name
