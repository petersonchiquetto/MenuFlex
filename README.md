# **MenuFlex** 🍽️🚀

**Description:**  
MenuFlex is an advanced Python application for creating and managing digital menus. It utilizes **APIs, inheritance, polymorphism, and advanced techniques** to offer a dynamic and efficient solution for restaurants. Ideal for those looking to modernize and optimize menu management. 🌟

---

## **Features** ✨  

- **Intuitive digital menu management** 📱  
- **Integration with external APIs** to fetch real-time data 🌍  
- Application of **OOP principles** (Inheritance, Polymorphism) 💻  
- **Advanced Python techniques** to optimize performance and code structure ⚡  

---

## **Technologies Used** 🛠️  

- **Python** (recommended version: 3.10+) 🐍  
- **FastAPI** or **Django** (for building REST APIs) ⚡  
- **SQLite** or **PostgreSQL** (if data persistence is needed) 🗄️  
- **Requests** (for consuming external APIs) 🌐  
- **JSON** (for saving and processing data) 📄

---

## **Installation** 🔧  

1️⃣ Clone the repository:  
```bash
git clone https://github.com/petersonchiquetto/MenuFlex.git
```

2️⃣ Navigate to the project folder:  
```bash
cd MenuFlex
```

3️⃣ Create and activate a virtual environment:  
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use: venv\Scripts\activate
```

4️⃣ Install dependencies:  
```bash
pip install -r requirements.txt
```

---

## **How to Use** 🏃‍♂️  

Once installed, run the project with the following command:

```bash
python main.py
```

Or, if you're building an API with **FastAPI** or **Django REST Framework**, refer to the **Architecture and Techniques** section below for setup instructions. 🔧

---

## **Architecture and Advanced Python Techniques** 🧠  

This project uses several advanced Python techniques and libraries to create a robust and scalable solution:

### **1. Consuming APIs with `requests`** 🌐  
The `requests` library is used to make HTTP requests to external APIs, allowing the system to retrieve dynamic data from other services.  

**Example:**  
```python
import requests
response = requests.get('https://guilhermeonrails.github.io/api-restaurantes/restaurantes.json')
```

### **2. Handling JSON Data** 📄  
We use `json.loads()` and `json.dump()` to work with JSON data. The code processes the API response, extracts restaurant information, and saves each restaurant's menu in separate `.json` files.

### **3. Optimized Data Structures** 📊  
The application uses **dictionaries** (`dict`) and **lists** (`list`) to store and organize data efficiently. In the example below, restaurants are grouped by name, and menu items are stored as a list.

```python
dados_restaurante = {}
for item in dados_json:
    nome_do_restaurante = item['Company']
    if nome_do_restaurante not in dados_restaurante:
        dados_restaurante[nome_do_restaurante] = []
    
    dados_restaurante[nome_do_restaurante].append({
        "item": item['Item'],
        "price": item['price'],
        "description": item['description']
    })
```

### **4. Error Handling** ⚠️  
The code checks the HTTP status code before processing the data. This ensures that the system operates only with valid data.

---

## **FastAPI or Django: Transforming the Project into an API** 🔄  

If you'd like to transform this project into a **RESTful API**, both **FastAPI** and **Django REST Framework** are great options. Here are the details of how you could use each:

### **FastAPI (Fast and Modern)** ⚡  
FastAPI is an excellent choice for building high-performance APIs. With **asynchronous** support and **Pydantic** data validation, it’s perfect for high-demand APIs.

#### Example implementation with **FastAPI**:
```python
from fastapi import FastAPI
import requests

app = FastAPI()

@app.get("/restaurantes")
def get_restaurants():
    url = 'https://guilhermeonrails.github.io/api-restaurantes/restaurantes.json'
    response = requests.get(url)
    
    if response.status_code == 200:
        return response.json()
    return {"error": "Failed to fetch data"}
```

To run the FastAPI server, use the following command:
```bash
uvicorn main:app --reload
```

### **Django REST Framework (Ideal for Scalable Projects)** 📈  
If you are building a larger system and need data persistence with a database, Django REST Framework is the right choice. It provides integrated **serializers**, **views**, and **ORM models**.

#### Example implementation with **Django REST Framework**:
```python
from rest_framework.response import Response
from rest_framework.decorators import api_view
import requests

@api_view(['GET'])
def list_restaurants(request):
    url = 'https://guilhermeonrails.github.io/api-restaurantes/restaurantes.json'
    response = requests.get(url)
    
    if response.status_code == 200:
        return Response(response.json())
    return Response({"error": "Failed to fetch data"}, status=500)
```

---

## **Contributing** 🤝  
Contributions are welcome! If you have ideas to improve the project, feel free to **fork** the repository, make your changes, and submit a **pull request**.

---

## **License** 📜  
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
