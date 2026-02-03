# Patient Management System API

## Description

A FastAPI-based REST API for managing patient records. This API allows users to view patient information, including personal details, BMI calculations, and health verdicts based on BMI categories.

## Features

- Retrieve all patient records
- Retrieve specific patient details by ID
- Automatic BMI calculation and health assessment
- Simple JSON-based data storage

## Installation

1. Clone the repository:
   ```
   git clone <repository-url>
   cd fastAPI
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

## Usage

1. Run the FastAPI server:
   ```
   uvicorn main:app --reload
   ```

2. Access the API at: `http://127.0.0.1:8000`

3. View interactive API documentation at: `http://127.0.0.1:8000/docs`

## API Endpoints

### GET /
Returns a welcome message.

**Response:**
```json
{
  "message": "Patient Management System API."
}
```

### GET /about
Returns information about the API.

**Response:**
```json
{
  "message": "This API manages patient records and appointments."
}
```

### GET /view
Retrieves all patient records.

**Response:**
```json
{
  "P001": {
    "name": "Ananya Sharma",
    "city": "Guwahati",
    "age": 28,
    "gender": "female",
    "height": 1.65,
    "weight": 90.0,
    "bmi": 33.06,
    "verdict": "Obese"
  },
  ...
}
```

### GET /view/{patient_id}
Retrieves details for a specific patient by ID.

**Parameters:**
- `patient_id` (string): The unique ID of the patient (e.g., "P001")

**Response:**
```json
{
  "name": "Ananya Sharma",
  "city": "Guwahati",
  "age": 28,
  "gender": "female",
  "height": 1.65,
  "weight": 90.0,
  "bmi": 33.06,
  "verdict": "Obese"
}
```

**Error Response (404):**
```json
{
  "detail": "Patient not found"
}
```

## Data Structure

Patient data is stored in `patient.json` with the following structure:

```json
{
  "PATIENT_ID": {
    "name": "string",
    "city": "string",
    "age": "integer",
    "gender": "string",
    "height": "float",
    "weight": "float",
    "bmi": "float",
    "verdict": "string"
  }
}
```

### BMI Categories
- Underweight: BMI < 18.5
- Normal: 18.5 ≤ BMI < 25
- Overweight: 25 ≤ BMI < 30
- Obese: BMI ≥ 30

## Dependencies

- FastAPI
- Pydantic
- Uvicorn (for running the server)

See `requirements.txt` for full list.

## Contributing

Feel free to submit issues and pull requests.

## License

This project is licensed under the MIT License.
