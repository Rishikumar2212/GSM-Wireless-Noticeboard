🔷 Project Title: "GSM-Based Wireless Notice Board using Arduino UNO"

📄 Project Description: 
This project is a wireless notice board system using an Arduino UNO, GSM module, and 16x2 LCD display. The system receives SMS messages via the GSM module and displays them on the LCD. It acts like a digital notice board which can be updated from anywhere just by sending an SMS. This is highly useful in: Schools or colleges for displaying updates Offices or factories for alerts Public info systems without Wi-Fi

🔧 Key Features: 
Feature Description 📲 GSM SMS Reading Reads SMS sent to SIM card 📟 16x2 LCD Display Shows messages to users 🧠 Arduino UNO Main controller to process logic 💡 LED Indicator Shows system activity 🔢 SMS Format Parsing Only messages between # and * are displayed 🔌 No Internet Required Works purely on GSM SMS

🧠 How it Works (Flow): 
Cellular Network [User Sends SMS] → GSM Module → PC/Java Program → Arduino UNO/Microcontoller with LCD → Extracts Message → LCD Displays it

🧾 Components Used: Component Quantity Purpose Arduino UNO 1 Main brain GSM Module (SIM800L/SIM900A) 1 Receives SMS SIM Card 1 Receives the message 16x2 LCD Display 1 Shows messages Potentiometer 1 LCD contrast control Power Supply (5V 2A) 1 GSM Module Power Jumper Wires + Breadboard -- Connections LED 1 Status Indication

🧾 Code Explanation:

1. Program Setup and Input
Import: import java.util.Scanner; imports the Scanner class, which is used to read input from the console (keyboard).
Input Initialization: Scanner scanner = new Scanner(System.in); creates a Scanner object linked to System.in, which is the standard input stream (keyboard).
Prompt: System.out.println("Enter message (format: #message*):"); provides the user instructions on the expected format of the message.
Continuous Listening: while (true) creates an infinite loop, causing the program to continuously wait for and process new input, simulating the listening action of the serial communication loop.
Reading Input: String input = scanner.nextLine(); waits for the user to type a full line of text and press Enter, treating the line as the "received message."

2. Message Processing Loop
Parsing Call: String message = extractMessage(input); sends the user's input string to the extractMessage method for processing.
Validation: if (!message.isEmpty()) { ... } checks if the extractMessage method successfully returned a message (a non-empty string).
Success Output: If valid, it prints the extracted message to the console: "Message Received: " + message.
Failure Output: If the message is an empty string (meaning the #...* format was missing), it prints: "No valid message found."

3. extractMessage Method (The Core Logic)
This static method contains the logic for finding and isolating the notice content.
Delimiter Search:
int start = input.indexOf('#'); finds the index (position) of the start delimiter (#).
int end = input.indexOf('*'); finds the index (position) of the end delimiter (*).
Format Check: if (start != -1 && end != -1 && end > start) checks three conditions simultaneously:
start != -1: The # was found.
end != -1: The * was found.
end > start: The end delimiter appears after the start delimiter.
Extraction: If the format check passes, return input.substring(start + 1, end); extracts and returns the message content. It starts the substring one character after the # (start + 1) and stops one character before the * (end).
Default Return: return ""; returns an empty string if the message format is invalid.

✅ Example SMS: #Hello Rishi* This message will be shown on LCD as:
Output : Hello Rishi

💡 Real-World Applications: Wireless Notice Boards (schools, offices) Emergency Alert Display System Factory Info System (low signal areas) Smart village information.

📌 Summary: ✅ Feature Status Works on Arduino UNO
             ✅ No Internet needed
             ✅ SMS based control
             ✅ Display via LCD
             ✅ Clean message parser
