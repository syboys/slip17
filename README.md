# slip17


Q.1 Write a Java Program to implement Abstract Factory Pattern for Shape interface.

Q.2. Write a python program to implement Multiple Linear Regression for a given dataset.

Q.3. Write node js application that transfer a file as an attachment on web and enables
browser to prompt the user to download file using express js.


Q.1 Write a Java Program to implement Abstract Factory Pattern for Shape interface.

:
interface Shape
{
void draw();
}
class RoundedRectangle implements Shape
{
 public void draw()
 {
 System.out.println(" Inside RR");
 }
}
class RoundedSquare implements Shape
{
 public void draw()
 {
 System.out.println(" Inside RS");
 }
}
class Rectangle implements Shape
{
 public void draw()
 {
 System.out.println(" Inside Simple R");
 }
}
class Square implements Shape
{
 public void draw()
 {
 System.out.println(" Inside Simple Sq");
 }
}
abstract class AbstractFactory
{
 abstract Shape getShape( String st);
}
class ShapeFactory extends AbstractFactory
{
 public Shape getShape( String st)
 {
 if(st.equalsIgnoreCase("Rectangle"))
 { return new Rectangle();}
 else if(st.equalsIgnoreCase("Square"))
 { return new Square();}
 return null;
 }
}
class RoundedShapeFactory extends AbstractFactory
{
 public Shape getShape( String st) 
{
 if(st.equalsIgnoreCase("Rectangle"))
 { return new RoundedRectangle();}
 else if(st.equalsIgnoreCase("Square"))
 { return new RoundedSquare();}
 return null;
 }
}
class FactoryProducer
{
 public static AbstractFactory getFactory(boolean rounded)
 {
 if (rounded)
 { return new RoundedShapeFactory();}
 else
 { return new ShapeFactory();}
 }
}
public class Main
{
 public static void main(String[]args)
 {
 AbstractFactory shapeFactory=FactoryProducer.getFactory(false);
 Shape shape1=shapeFactory.getShape("Rectangle");
 shape1.draw();
 Shape shape2=shapeFactory.getShape("SQuare");
 shape2.draw();

 AbstractFactory shapeFactory1=FactoryProducer.getFactory(true);
 Shape shape3=shapeFactory1.getShape("REctangle");
 shape3.draw();

 Shape shape4=shapeFactory1.getShape("square");
 shape4.draw();
 }
} 



Q.2. Write a python program to implement Multiple Linear Regression for a given dataset.

:import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("dataset.csv")

# Split the data into features (X) and target (y)
X = df.drop("target", axis=1)
y = df.target

# Split the data into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Create the model
model = LinearRegression()

# Train the model on the training data
model.fit(X_train, y_train)

# Make predictions on the test data
y_pred = model.predict(X_test)

# Calculate the mean squared error
mse = mean_squared_error(y_test, y_pred)

# Print the results
print("Mean Squared Error:", mse)
print("Coefficients:", model.coef_)

print("Intercept:", model.intercept_)

q3)Write node js application that transfer a file as an attachment on web and enables
browser to prompt the user to download file using express js.
:
var express = require('express');
var app = express();
var PORT = 3000;

app.get('/', function(req, res){
 res.download('Unknown_file.txt', function(error){
 console.log("Error : ", error)
 });
});

app.listen(PORT, function(err){
 if (err) console.log(err);
 console.log("Server listening on PORT", PORT);
});
