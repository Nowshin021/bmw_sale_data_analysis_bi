# Dataset_overview

 This dataset contains information about various cars, likely from a car dealership or a sales platform. Each row represents a different car, and the columns provide specific details about each vehicle.

# Dataset Explanation
 Model: This column identifies the specific car model, such as X6, i8, 5 Series, and M3.

 Year: The manufacturing year of the car is provided here.

 Region: This indicates the geographical sales region, which in this case is consistently North America.

 Color: The car's exterior color is listed, with all entries showing Red.

 Fuel_Type: The type of fuel the car uses is specified, which is uniformly Diesel across the dataset.

 Transmission: This column describes the type of transmission, with all cars having an Automatic transmission.

 Engine_Size_L: This is the size of the car's engine, measured in liters.

 Mileage_KM: The total distance the car has traveled, in kilometers.

 Price_USD: The selling price of the car in US dollars.

 Sales_Volume: This represents the number of units sold for that specific model.

 Sales_Classification: The sales performance is categorized, with all entries being Low.

 engine size group: The engine size is grouped into categories like Small, Medium, and Large.

 regional_sale_status: This column indicates the sales status within the region, with all entries showing LOW Sale Region.


# bmw_sale_data_analysis_bi
Power Bi Data analysis on BMW Sales over the  years In Different Regions.
This Power BI dashboard provides insights into the sales performance of a car brand, likely BMW, by presenting a comprehensive overview of various key metrics.

What is the total revenue and number of cars sold over time?

What is the overall financial performance and total sales volume?

What is the regional sales status?

What is the breakdown of sales volume between high and low-performing periods?

Which car models are the best and worst sellers?

How are car sales distributed across different fuel types?

# Region Wise Sale analysis 
<img width="1297" height="721" alt="image" src="https://github.com/user-attachments/assets/747a8620-6b45-4b56-907f-d566e1b5bbf1" />

# Model Wise Sale Analysis
How has the average sales volume changed on a yearly basis?

What is the total sales volume and revenue for each type of fuel?

Which car models have the highest and lowest average mileage?

Which car models generate the most and least revenue?

<img width="1277" height="716" alt="image" src="https://github.com/user-attachments/assets/dbe3152c-ab12-413c-8dae-237c255d57c6" />



# DAX Queries :
1. Took the Engine Size and devided them into three groups to extract valuable insights

engine size group = 
SWITCH(
    TRUE(),
    bmw_sale_data[Engine_Size_L] >= 1.5   && bmw_sale_data[Engine_Size_L] <= 3.0 , "Small",
    bmw_sale_data[Engine_Size_L] >= 3.1   && bmw_sale_data[Engine_Size_L] <= 4.0 , "Medium",
    bmw_sale_data[Engine_Size_L] >= 4.1   && bmw_sale_data[Engine_Size_L] <= 5 , "Large", BLANK()
)

3. To see which region is doind well in terms of BMW sales , Devided the regional sale classification

regional_sale_status = 
VAR high_sales =
    CALCULATE (
        COUNTROWS ( bmw_sale_data ),
        bmw_sale_data[Sales_Classification] = "High"
    )
VAR low_sales =
    CALCULATE (
        COUNTROWS ( bmw_sale_data ),
        bmw_sale_data[Sales_Classification] = "Low"
    )
RETURN
    IF (
        high_sales > low_sales,
        "🔥 HIGH Sale Region",
        "⬇️ LOW Sale Region "
    )



