# bmw_sale_data_analysis_bi
Power Bi Data analysis on BMW Sales over the  years In Different Regions.

Region Wise Sale analysis 
<img width="1297" height="721" alt="image" src="https://github.com/user-attachments/assets/747a8620-6b45-4b56-907f-d566e1b5bbf1" />

Model Wose Sale Analysis
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

2. To see which region is doind well in terms of BMW sales , Devided the regional sale classification

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



