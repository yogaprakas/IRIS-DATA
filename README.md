# 🌸 Iris Flower Prediction API — Request Flow

This document explains the complete request flow of the **Iris Flower Prediction API**, from receiving flower measurements to returning the predicted Iris species.

---

## 1. 📥 Request

The user sends flower measurements to the `/predict` API endpoint.

The request must contain the following four features:

| Feature        | Description         |
| -------------- | ------------------- |
| `sepal_length` | Length of the sepal |
| `sepal_width`  | Width of the sepal  |
| `petal_length` | Length of the petal |
| `petal_width`  | Width of the petal  |

### Example Input

```json
{
  "sepal_length": 5.1,
  "sepal_width": 3.5,
  "petal_length": 1.4,
  "petal_width": 0.2
}
```

⬇️

## 2. ✅ Input Validation

Before sending the data to the Machine Learning model, the API validates the request.

The API checks that:

* All four required measurements are provided.
* All values are valid numbers.
* The input follows the expected JSON format.

If any required value is missing or invalid, the API returns an appropriate error response.

⬇️

## 3. 🤖 Machine Learning Model

If the input passes validation, the four measurements are passed to the trained Machine Learning model.

The model analyzes the measurements and predicts one of the following Iris species:

* 🌱 **Setosa**
* 🌿 **Versicolor**
* 🌸 **Virginica**

⬇️

## 4. 📤 Response

After making the prediction, the API returns the result in **JSON format**.

### Example Response

```json
{
  "species": "setosa",
  "confidence": 0.98
}
```

### Response Fields

| Field        | Description                       |
| ------------ | --------------------------------- |
| `species`    | The predicted Iris flower species |
| `confidence` | The model's confidence score      |

In this example, the model predicts **Setosa** with a confidence score of **98%**.

---

## 🔄 Request Flow

```text
┌──────────────────────┐
│        User          │
│  Flower Measurements │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│    POST /predict     │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│   Input Validation   │
└──────────┬───────────┘
           │
      ┌────┴─────┐
      │           │
    Valid       Invalid
      │           │
      ▼           ▼
┌────────────┐  ┌─────────────┐
│ ML Model   │  │ Error       │
│ Prediction │  │ Response    │
└─────┬──────┘  └─────────────┘
      │
      ▼
┌──────────────────────┐
│   JSON Response      │
│ Species + Confidence │
└──────────────────────┘
```

### 🔗 Overall Flow

**Request → Validation → ML Model → Prediction → JSON Response**
