sudo apt-get install python3-venv    # If needed
python3 -m venv env

pip3 install flask



Ctrl + Shift + P

    Python: Select Interpreter
        Choose the one you have into "env" folder


source env/bin/activate

# Execute
python -m flask run

    # This will search for app.py and start the server into development mode

Run the app in the debugger

Go to:
    http://127.0.0.1:5000/hello/VSCode


Ctrl + Shift + F5: Start debugging

Ctrl + F5: Stop debugging


# To create code snippets:
In VS Code, select the File (Windows/Linux) or Code (macOS), menu, then select Preferences > User snippets.

It will be like this below:
```
{
	// Place your snippets for python here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same ids are connected.
	// Example:
	"newbp": {
		"prefix": "createbp",
		"body": [
			"from flask import Blueprint, jsonify, request, make_response",
			"from flask_jwt_extended import (jwt_required)",
			"from flask_cors import cross_origin",
			"from logic.error_handler import ExceptionHandler",
			"#",
			"#",
			"$1_api = Blueprint('$2_api', __name__)",
			"@propietarios_api.route('/api/propietarios/create', methods=['POST'])",
			"#",
			"#",
			"@cross_origin()",
			"@jwt_required",
			"def index():",
			"    args = request.form",
			"    try:",
			"        # Starts here",
			"        response = make_response(jsonify(results), 200)",
			"    except Exception as e:",
			"        eh = ExceptionHandler.handle(e)",
			"        response = make_response(eh.get('message'), eh.get('error_number'))",
			"    ",
			"    return response",
			"$3"
		],
		"description": "Add the required code for a new Blueprint File",
	},
	"createLogic": {		
		"prefix": "createLogicFile",
		"description": "Add the required code for a new Logic File",
		"body": [
			"from sqlalchemy.orm import Session",
			"from extensions.db import DB",
			"from logic.utils import Utils",
			"#",
			"#",
			"class $1:",
			"",
			"@staticmethod",
			"def METHOD_NAME(propietario, usuario):",
			"    # code here",
			"    result = ({})",
			"    session = Session(DB.engines['dev'])",
			"    try:",
			"        #",
			"        return result",
			"    except Exception as e:",
			"         session.rollback()",
			"    ",
		],
	}
}
```
# flask-debug-example
