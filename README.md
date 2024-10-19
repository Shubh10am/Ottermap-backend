
```markdown
# Shop API

Welcome to the Shop API! This API provides endpoints for managing shop details, including registration, token creation, and searching for shops based on geographical location. The API uses Flask, Flask-RESTx, and MongoDB as the database.

## Features

- 🛠️ **Create Access Token**: Secure your API access with JWT tokens.
- 🏪 **Register a Shop**: Add new shop details to the database.
- 🔍 **Search Shops**: Retrieve a list of shops based on user location, sorted by distance.

## Requirements

- 🐍 Python 3.x
- 📦 Flask
- 🔑 Flask-JWT-Extended
- 🛠️ Flask-RESTx
- 🗄️ PyMongo
- 🐘 MongoDB

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Shubh10am/Ottermap-backend.git
   cd shop-api
   ```

2. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up your MongoDB database.

4. Configure your environment variables for database connection and JWT secret.

## API Endpoints

### 1. Create Access Token

- **Endpoint**: `/shops/create-token`
- **Method**: `POST`
- **Description**: Generates a JWT access token for API access.
- **Credentials**: 
  - Username: `shubh`
  - Password: `shubh@12`

#### Response Example
```json
{
    "data": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTcyOTI3MzE1NiwianRpIjoiNTkzODNiNzItMzI0Yy00ODRlLWEwZmUtY2U4ZGJkMDEzNDY2IiwidHlwZSI6ImFjY2VzcyIsImlkZW50aXR5Ijoic2h1YmgiLCJuYmYiOjE3MjkyNzMxNTYsImV4cCI6MTcyOTI3NDA1Nn0.hMSU5uDnCDFvjx6R82QjgBr7tZKieVEt4mmajCIQ7IE",
    "status_code": 200,
    "message_code": "success",
    "message": "Token Generated successfully",
    "success": true
}
```

### 2. Register a Shop

- **Endpoint**: `/shops/register`
- **Method**: `POST`
- **Authorization**: Bearer token (JWT)
- **Request Body**:
  - `name`: Name of the shop
  - `latitude`: Latitude of the shop (-90 to 90)
  - `longitude`: Longitude of the shop (-180 to 180)

#### Response Example
```json
{
    "data": {
        "shop_id": "shop_uFloRgtVwzurtiPIprBX",
        "name": "Shop E",
        "latitude": 19.34,
        "longitude": 110.78
    },
    "status_code": 200,
    "success": true,
    "message": "Shop Details Saved Successfully",
    "message_code": "success"
}
```

### 3. Search Shops

- **Endpoint**: `/shops/search`
- **Method**: `GET`
- **Query Parameters**:
  - `latitude`: User's latitude
  - `longitude`: User's longitude
- **Description**: Returns a list of shops sorted by distance from the user's location.

#### Response Example
```json
{
    "data": [
        {
            "name": "Shop D",
            "distance": 0.0
        },
        {
            "name": "Shop C",
            "distance": 10696.51
        },
        {
            "name": "Shop C",
            "distance": 10696.51
        },
        {
            "name": "Shop D",
            "distance": 10696.51
        }
    ],
    "status_code": 200,
    "message_code": "success",
    "message": "Shops fetched successfully",
    "success": true
}
```

## Direct API Access

You can also hit the API directly at the deployed URL: [https://ottermap-backend.onrender.com](https://ottermap-backend.onrender.com).

## Utilities

### Haversine Function

The Haversine function calculates the distance between two geographical points on the Earth given their latitude and longitude. This method is used to sort the shops based on their distance from the user's location.

```python
def haversine(lat1, lon1, lat2, lon2):
    R = 6371  # Earth radius in kilometers
    dlat = radians(lat2 - lat1)
    dlon = radians(lon2 - lon1)
    a = sin(dlat / 2) ** 2 + cos(radians(lat1)) * cos(radians(lat2)) * sin(dlon / 2) ** 2
    c = 2 * atan2(sqrt(a), sqrt(1 - a))
    return R * c
```

## Contributing

🤝 Feel free to fork the repository, make changes, and submit a pull request. Any improvements, bug fixes, or features are welcome!

## License

📜 This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- 🍔 [Flask](https://flask.palletsprojects.com/)
- 🏗️ [Flask-RESTx](https://flask-restx.readthedocs.io/)
- 🔒 [Flask-JWT-Extended](https://flask-jwt-extended.readthedocs.io/)
- 📊 [MongoDB](https://www.mongodb.com/)
```
