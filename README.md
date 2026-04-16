## Data Persistence and API Integration

## How to Run
### 1. Clone the repo
`git clone https://github.com/Mitchie2910/GenderizeIntegration.git`

### 2. Build the project
`mvn clean install`

### 3. Run the application
`mvn spring-boot:run`


## EndPoints

### POST api/profiles

Creates Profile from name

Request:

```json
{ "name": "ella" }
```

Success(201)

```json
{
  "status": "success",
  "data": {
    "id": "uuid-v7",
    "name": "ella",
    "gender": "female",
    "gender_probability": 0.99,
    "sample_size": 1234,
    "age": 46,
    "age_group": "adult",
    "country_id": "DRC",
    "country_probability": 0.85,
    "created_at": "2026-04-01T12:00:00Z"
  }
}
```

Idempotent Response(200)

```json
{
  "status": "success",
  "message": "Profile already exists",
  "data": {}
}
```

### GET api/profiles{id}

```json
{
  "status": "success",
  "data": {}
}
```

### GET api/profiles{id}

Filters `gender`, `country_id` and `age_group`

```json
{
  "status": "success",
  "count": 2,
  "data": []
}
```

### GET api/profiles{id}

204 No Content

## Errors

### Validation

- 400 -> missing/empty name
- 422 -> invalid input

### Not Found

- 404 -> profile not found

### Error Structure

```json
{
  "status": "error",
  "message": "error message"
}
```
