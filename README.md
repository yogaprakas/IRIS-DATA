\# Iris Flower Prediction API \- Request Flow

\#\# 1\. Request

The user sends the flower measurements to the \`/predict\` API.

The request contains:  
\- Sepal length  
\- Sepal width  
\- Petal length  
\- Petal width

For example, the user might send measurements like 5.1, 3.5, 1.4, and 0.2.

↓

\#\# 2\. Validation

The API checks the information before using it.

It makes sure that:  
\- All four measurements are provided.  
\- The values are numbers.  
\- The input is in the expected format.

If something is missing or invalid, the API returns an error instead of sending it to the model.

↓

\#\# 3\. Model

If the input is valid, the four measurements are sent to the trained Machine Learning model.

The model looks at the measurements and predicts which Iris species the flower belongs to:

\- Setosa  
\- Versicolor  
\- Virginica

↓

\#\# 4\. Response

The API sends the prediction back to the user in JSON format.

For example:

{  
    "species": "setosa",  
    "confidence": 0.98  
}

This means the model predicted that the flower is Setosa with a confidence score of 0.98.  
