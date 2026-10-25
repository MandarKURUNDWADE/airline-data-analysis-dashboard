# Airline Data Management and Analysis Using Power BI

## Project Overview

This project uses **Power BI** to analyze airline operations data and
provide insights into flight performance, passenger distribution, and
ticket booking status. The goal is to support operational efficiency and
better customer experience through data-driven reporting.

## Objectives

-   Clean and transform data using **Power Query**.
-   Build relationships between flight, passenger, and ticket tables.
-   Create calculations and metrics using **DAX**.
-   Develop interactive dashboards for analysis.
-   Configure **Row-Level Security (RLS)** and scheduled refresh in
    Power BI Service.

## Datasets

1.  **Flight_Information** --- `FlightID`, `FlightNumber`, `Airline`,
    `Destination`, `Status`
2.  **Passenger_Information** --- `PassengerID`, `FlightID`,
    `SeatNumber`
3.  **Ticket_Information** --- `TicketID`, `FlightID`, `BookingStatus`

## Methodology

### 1. Data Preparation and Cleaning

-   Removed duplicates and handled missing values.
-   Set appropriate data types for fields.
-   Used Power Query Editor for transformation.

### 2. Data Modeling

-   Created one-to-many relationships using `FlightID`.
-   Reviewed referential integrity and cross-filter direction.

### 3. Flight Performance Classification

-   Created `Flight_Performance` to classify flights as **Best** (On
    Time) or **To Be Improved** (Delayed/Cancelled).
-   Extracted flight numbers using **Column from Examples**.

### 4. DAX Calculations

``` dax
Total_Passengers =
COUNT ( Passenger_Information[PassengerID] )

Total_Tickets_Booked =
COUNT ( Ticket_Information[TicketID] )

Best_Flights =
FILTER (
    Flight_Information,
    Flight_Information[Flight_Performance] = "Best"
)
```

### 5. Dashboard and Visualizations

-   **Stacked bar chart:** Passenger count by airline.
-   **Donut chart:** Ticket booking status.
-   **Heatmap:** Flights by airline and destination.
-   **Slicers:** Airline and destination.
-   **Tooltips and navigation buttons:** Support more detailed
    exploration.

### 6. Power BI Service Deployment

-   Published to the **AirDMA** workspace.
-   Configured RLS for **Airline A**.
-   Set scheduled refresh daily at **5 PM**.

## Key Insights

-   **Airline D** had the highest passenger count (**28**).
-   **Los Angeles** was the most popular destination (**42
    passengers**).
-   **22% of tickets** had a **Pending** status, indicating a potential
    opportunity to improve booking confirmation.

## Recommendations

1.  Investigate delays among flights classified as **To Be Improved**.
2.  Improve ticket confirmation processes to reduce pending bookings.

## License

This project is licensed under the **MIT License**.
