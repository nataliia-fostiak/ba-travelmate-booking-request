# Feature: The booking process (Booking flow):
 from choosing a room to payment and receiving confirmation.
## Use Case: The booking process. The main participants in the diagram are the User, the Hotel System, and the Database / External Services. The diagram depicts the complete online hotel booking scenario, starting from browsing the hotel details, selecting a room and dates, entering personal information, and processing the payment, up to successfully booking the room and sending a confirmation to the user's email.
```mermaid
sequenceDiagram
    autonumber
    actor User
    participant System as Hotel System
    participant Database as Database / External Services

    %% Step 1
    User->>System: Open hotel's page
    System-->>User: Display hotel details (room types, photos, ratings, reviews)

    %% Step 2
    User->>System: Open photo gallery
    System-->>User: Display hotel photos

    %% Step 3
    User->>System: Open rating and reviews
    System-->>User: Display hotel rating and reviews

    %% Step 4
    User->>System: Open list of available rooms & click desired room
    System-->>User: Select relevant room

    %% Step 5
    User->>System: Select check-in and check-out dates
    System->>Database: Check room availability for selected dates
    Database-->>System: Return availability status
    System-->>User: Confirm room is available for dates

    %% Step 6
    User->>System: Enter personal details & click 'Save'
    System->>Database: Save personal information

    %% Step 7
    User->>System: Review booking price
    System-->>User: Display total booking cost (room price, taxes, fees)

    %% Step 8
    User->>System: Click on desired payment method
    System-->>User: Select payment method

    %% Step 9
    User->>System: Click the 'Pay' button
    System-->>User: Display message asking for payment confirmation

    %% Step 10 & 11
    User->>System: Click the 'Confirm' button
    System->>Database: Process the payment
    Database-->>System: Send confirmation of successful payment

    %% Step 12 & 13
    System->>Database: Proceed with room booking
    System->>Database: Send booking details to the hotel
    System-->>User: Send booking confirmation to email & display booking in account
    ```