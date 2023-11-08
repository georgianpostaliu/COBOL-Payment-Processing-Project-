# COBOL-Payment-Processing-Project-
Summary:

This COBOL program serves as a payment processor, accepting payment details from users, validating the input, performing currency conversion, deducting processing fees, and categorizing payments into accepted and rejected transactions. It handles multiple card types, countries, and rejection scenarios, ensuring accurate processing and clear reporting of accepted and rejected payments. The structured approach allows for easy modification and extension to accommodate additional payment processing logic or integration into larger financial systems.

This COBOL project, identified as COBIF01, is designed to process payment information provided through user input. The program reads payment data for various transactions, validates the input, calculates the payment amount based on card type and country, and categorizes the transactions into accepted and rejected payments. The processed payment details are then displayed in a specified format. Let's break down the structure and functionality of this COBOL program:
Identification Division:

    Program ID: COBIF01

Environment Division:

    Configuration Section: Configures special names, setting the console as CNSL.

Data Division:

    Working-Storage Section:
        WS-RECORD: Represents a sample input record with a fixed length of 23 characters.
        WS-OUTPUT-FILE: Contains variables to store accepted payment data in a specific format.
        WS-REJECT-FILE: Contains variables to store rejected payment data in a specific format, including rejection reasons.
        WS-INPUT2: Contains variables for input payment data, including payee name, currency, amount, card type, card number, and country.
        WS-RATE-EURGBP, WS-RATE-USDGBP, WS-RATE-RONGBP, WS-RATE-BGNGBP: Variables holding currency conversion rates for different countries.
        WS-COUNTER: Counter variable to control the number of iterations in the payment processing loop.

Procedure Division:

    Processing Logic:
        The program enters a loop, accepting payment details 8 times using the PERFORM UNTIL WS-COUNTER = 8 ACCEPT WS-INPUT2 statement.
        Within each iteration, the program captures the payee name, currency, payment amount, card type, card number, and country from the user.
        The program validates the card type and country, performs currency conversion based on the card type and country, deducts processing fees, and categorizes the transaction as accepted or rejected.
        Processed payment details are stored in the WS-OUTPUT-FILE for accepted payments or the WS-REJECT-FILE for rejected payments.
    Output:
        Accepted payment details (name, converted amount) are displayed if the card type is not DIN (Diners Club) using the DISPLAY WS-OUTPUT-FILE UPON CNSL statement.
        Rejected payment details (card number, amount, country, rejection reason) are displayed for rejected payments using the DISPLAY WS-REJECT-FILE UPON CNSL statement.
        The program stops execution after processing the input payments (STOP RUN).
