# Smart-Activity-Reminder

**By:** Nohemy Oropeza Graffe

**Student credentials from Linnaeus University:** no222ix

**Project overview**

The Smart Activity Reminder is a personalized assistant device that helps individuals manage essential daily activities, enhancing productivity and well-being by providing timely reminders without the distractions of a smartphone.

**Time it might take to do (approximation)**

Around 24 applied hours

**Objective of the project**

The purpose of this device is to assist individuals, particularly those with ADHD (myself included), in easily managing daily activities like drinking the right amount of water, exercising, and maintaining productive time for work or study. While many smartphone apps and smartwatches offer reminders for such activities, they often require manual data entry, which can be tedious and distracting, especially for people with ADHD. This project aims to simplify that process by creating a device that automatically tracks these activities with minimal user intervention.

**Device Functionality:**

**1. Water Intake Reminder:**
A red LED light will turn on every 2 hours (from 8 AM to 8 PM) when temperatures are below 30°C, and every 1.5 hours when temperatures are above 30°C. The light stays on until the user presses the corresponding red button, indicating that a glass of water has been consumed. If the button is not pressed, the light will remain on until it resets for the next reminder cycle. The full system resets every 24 hours.

**2. Exercise Reminder:**
A yellow LED light will activate after midnight each day, staying on until the user presses the yellow button to indicate that they have exercised. This action logs the event. If the button is not pressed, the light will stay on until it resets at midnight for a new day.

**3. Productivity Timer:**
This function is designed to improve productivity by tracking the time spent on work or study. Pressing the green button starts the timer, turning on the green LED light. The light remains on until the button is pressed again to stop the timer. The total time logged is sent to another platform for tracking and analysis.

**Insights and Motivation:**
The device will collect data on water intake, exercise habits, and productivity, which will be displayed in a dashboard. This data can motivate users to improve their daily routines by allowing them to track their progress and compare it with previous days.

**Example of how the device could look in production:**

![image](https://github.com/user-attachments/assets/17dcee01-215e-44a8-9ae3-c009e4dbe3ce)


**Material**

All hardware was bought from Electrokit. I purchased the start kit for 399sek, in the following link:

https://www.electrokit.com/en/start-kit-applied-iot-at-linnaeus-university-2023 

From the kit i used the following materials:

**Raspberry Pi Pico WH:** I used this microcontroller for running the code that controls the LEDs, reads sensor data, makes the connection through bluetooth and manages reminders and timing functions.

![image](https://github.com/user-attachments/assets/105f5266-ed77-4867-886f-014a3c5b25db) 

**Solderless Breadboard 840 tie-points:** This breadboard allows to quickly and easily prototype the circuit without soldering. One can connect all components, like LEDs, sensors, and resistors, to test and build the circuit for the device.

![image](https://github.com/user-attachments/assets/a00ce845-e428-42d1-8ab5-732795ecb9a7)
  
**USB cable A male - micro B 5p male 1.8m:** This cable connects the Raspberry Pi Pico to a computer or power source, providing power and allowing to upload code to the microcontroller.

![image](https://github.com/user-attachments/assets/5da2aece-1a01-44d0-b9a8-a3b61d3612d9) 

**21 jumper wires in assorted lengths and colors (male/male):** These wires are used to connect the components on the breadboard to the Raspberry Pi Pico.

![image](https://github.com/user-attachments/assets/c28960ad-e40e-4310-81f6-5afe114841a7)
  
**2 LED 5mm diffuse 1500mcd in red and yellow:** These LEDs serve as visual indicators for the water intake and exercise reminders. The red LED indicates the need to drink water, and the yellow one signifies the exercise reminder.

![image](https://github.com/user-attachments/assets/dd0e98c9-666c-40e3-aaea-d201ee888827)

**1 LED 5mm green diffuse 80mcd:** This LED acts as an indicator for productive work time. It lights up when the timer function is activated, signaling that the user is currently in a work or study session.

![image](https://github.com/user-attachments/assets/78f1a083-1d76-4782-9932-e0bdff57692a)
  
**1 Digital temperature and humidity sensor DHT11:** This sensor measures the ambient temperature, allowing the device to adjust the water intake reminder frequency based on the temperature (e.g., more frequent reminders in hotter conditions).

 ![image](https://github.com/user-attachments/assets/dd593f0b-3b6f-45d0-96ef-befb3c2093f8) 
  
**3 Resistor carbon film 0.25W 1kohm (1k):** These resistors limit the current flowing through the LEDs, preventing them from burning out. Each LED in the circuit needs a resistor to ensure safe operation.

![image](https://github.com/user-attachments/assets/59473c71-c43c-4007-b82c-0bcf574a3918)


Aditionally, I also purchased from Electrokit, a kit of push buttons PCB 4 pins, with 4 units (red, yellow, green and blue), for only 19.20sek, and a Bluetooth module HC-06 for 76sek, which I used for connecting the pico to my mobile. 

**3 PCB Push buttons:**
**Green Button:** Starts/stops the productivity timer.
**Red Button:** Logs water intake, turning off the red LED.
**Yellow Button:** Logs exercise completion, turning off the yellow LED.

![image](https://github.com/user-attachments/assets/4b1d51da-d6e9-4bf0-890d-d11b5b1b9378) 

**1 Bluetooth module HC-06:** Enables wireless communication with a smartphone or computer.

![image](https://github.com/user-attachments/assets/753e6105-df0f-4082-9be4-375fb019e5c5) 

**Computer Setup and Uploading the Program to the Pico:**

I used Visual Studio Code (VSCode) as my Integrated Development Environment (IDE) and installed Node.js. After setting up both on my computer, I added the Pymakr extension in VSCode to communicate with the Raspberry Pi Pico running MicroPython. To begin programming the Pico, you first need to flash the MicroPython firmware. I downloaded the latest firmware release from the official website: https://micropython.org/download/RPI_PICO_W/.

Next, I connected the Pico to the USB cable. While holding down the BOOTSEL button, I connected the other end of the USB cable to my computer. A new drive called "RPI-RP2" appeared in my file system, representing the Raspberry Pi Pico's storage. I then copied and pasted the UF2 firmware file into this storage. Once the upload was complete, the Pico automatically disconnected and rebooted. To confirm that the board is ready, unplug and reconnect the USB cable.

With the updated firmware installed, I returned to VSCode. I clicked on the Pymakr logo in the lower left toolbar, where the Pico should appear as a connected device. I selected the option to connect and enabled development mode. I then created a new project and chose a designated folder on my computer to store all project files. Three key files were created: main.py, boot.py, and pymakr.conf.
The program for the Pico should be written in the main.py file. When the device is connected, running the program in VSCode will upload it to the Pico, where it will continue to operate as long as the device is powered.

**Transmitting the Data / Connectivity**
For my project, I decided to make the device dependent on my phone rather than directly connecting to Wi-Fi. To achieve this, I used a Bluetooth module on the Raspberry Pi Pico to connect with a Serial Bluetooth Terminal on my phone. The Pico sends data to my phone after each event (e.g., drinking water, exercising, working), where it is logged.

**Data Transmission Steps:**

**Event Triggered on Pico:** When an event occurs, such as pressing a button to log water intake, the data is transmitted via the Bluetooth module to the Serial Bluetooth Terminal app on my phone.

**Data Logging:** The data received by the Serial Bluetooth Terminal is stored in a specific folder on my phone.

**Data Transfer to the Cloud:** Using the Termux terminal app, a Python script runs periodically on my phone. This script retrieves the logged data and sends it to Adafruit IO, free tier, a cloud platform I've set up to handle the data.

**Cloud Storage and Visualization:** On Adafruit IO, I have created three feeds: exercise_status, glasses_of_water, and working_time. The data sent to these feeds is then used to generate a dashboard that visualizes the metrics.

**Wireless and Transport Protocols:**

**Wireless Protocol:** I used Bluetooth for short-range communication between the Pico and my phone. This choice was made to avoid the complexities of direct Wi-Fi setup on the Pico.

**Transport Protocol:** The data is sent from the phone to Adafruit IO using HTTP requests facilitated by the Python script in Termux. 

**Putting everything together**

**Wiring Details:**

**Raspberry Pi Pico WH:** Acts as the central microcontroller, managing all inputs and outputs. It is connected to the power supply via the USB cable.

**LEDs (Red, Yellow, Green):** Each LED is connected to a GPIO pin on the Pico. A 1kΩ resistor is connected in series with each LED to limit the current and prevent the LEDs from burning out.

**Push Buttons (Red, Yellow, Green):** Each button is connected to a GPIO pin and ground. When pressed, the button pulls the GPIO pin low, triggering an action in the Pico’s program.

**Bluetooth Module (HC-06):** The module is connected to the Pico's UART pins (TX and RX) to enable wireless communication with a smartphone. The VCC and GND of the module are connected to the 3.3V and ground pins of the Pico.

**Temperature and Humidity Sensor (DHT11):** Connected to a GPIO pin to read environmental data. The sensor's data pin is connected to the Pico, and it’s powered by the 3.3V and ground pins.

**Resistors, Current, and Voltage Considerations:**

**Resistors:** Each LED has a 1kΩ resistor to limit the current, ensuring that the LEDs operate safely without drawing too much current from the GPIO pins.

**Current and Voltage:** The Raspberry Pi Pico operates at 3.3V logic level, which is compatible with the HC-06 Bluetooth module and the DHT11 sensor. This setup minimizes power consumption and ensures that the components work within their specified voltage ranges.

**Development Setup vs. Production:**

**Development Setup:** The current setup is ideal for prototyping and testing on a solderless breadboard. This allows for easy modifications and troubleshooting during the development phase.

**Production Setup:** For a production setup, the components could be soldered onto a custom PCB for durability and reliability. The design is suitable for production with minimal changes.

**Circuit diagram (hand drawn :) )**

![image](https://github.com/user-attachments/assets/0921663c-b47b-47b1-a723-6fe6285c7df4)

**Pictures of the components connected to the Pico on the breadbord:**

![image](https://github.com/user-attachments/assets/f7e7a8cc-67cf-4d0c-a0cd-4b5155df7eb6)

![image](https://github.com/user-attachments/assets/d6d4914e-e5e8-4606-b899-33c74c610637)

**Program running in the Pico**

The project code on the Raspberry Pi Pico consists of two main files: `main.py` and `dht.py`. The `main.py` file handles the core logic of the device, including interaction with buttons, LEDs, and Bluetooth communication. The `dht.py` file provides a driver for reading data from DHT11 or DHT22 sensors, which measure temperature and humidity.

**This are the imported libraries in the main.py file:**

  ``` # Import necessary modules
from machine import Pin, UART
from utime import sleep, ticks_ms, ticks_diff, localtime
import dht
import json
```

**Core Functionalities:**

1. **`main.py` - Central Program Logic:**

   - **Bluetooth Communication Setup:**
     
     ```python
     uart = UART(0, baudrate=9600, tx=Pin(0), rx=Pin(1))
     ```
     - **Explanation**: This line initializes the UART interface to establish Bluetooth communication, which is used to send data from the Pico to a connected smartphone for logging and analysis.

   - **Button and LED Management:**
     ```python
     redLED = Pin(15, Pin.OUT)
     yellowLED = Pin(13, Pin.OUT)
     greenLED = Pin(11, Pin.OUT)
     redButton = Pin(17, Pin.IN, Pin.PULL_UP)
     yellowButton = Pin(21, Pin.IN, Pin.PULL_UP)
     greenButton = Pin(16, Pin.IN, Pin.PULL_UP)
     ```
     - **Explanation**: These lines configure the GPIO pins on the Pico for the LEDs and buttons. The LEDs provide visual reminders, while the buttons allow the user to log activities (e.g., drinking water, exercising, working).

   - **Event Handling and Data Logging:**
     ```python
     def send_uart_data(event, value=None):
         data = {"event": event, "timestamp": current_time_str()}
         if value is not None:
             data["value"] = round(value, 2) if isinstance(value, float) else value
         uart.write(json.dumps(data) + "\n")
     ```
     - **Explanation**: This function formats and sends event data (such as "drank_water" or "exercise_done") via Bluetooth. It includes a timestamp and, when applicable, the value associated with the event.

   - **DHT Sensor Integration:**
     ```python
     dht_sensor = dht.DHT11(Pin(22))
     ```
     - **Explanation**: The DHT11 sensor is initialized on GPIO pin 22. This sensor is used to measure the ambient temperature, which then adjusts the frequency of water intake reminders depending on whether the temperature is above or below a specified threshold.

2. **`dht.py` - DHT Sensor Driver:**

   - **Platform-Specific Imports:**
     ```python
     if hasattr(machine, "dht_readinto"):
         from machine import dht_readinto
     elif sys.platform == "rp2":
         from machine import dht_readinto
     else:
         dht_readinto = __import__(sys.platform).dht_readinto
     ```
     - **Explanation**: This code checks the platform on which the code is running and imports the appropriate method for reading data from the DHT sensor. This makes the driver compatible with multiple platforms, including the Raspberry Pi Pico.

   - **Sensor Data Reading and Validation:**
     ```python
     def measure(self):
         buf = self.buf
         dht_readinto(self.pin, buf)
         if (buf[0] + buf[1] + buf[2] + buf[3]) & 0xFF != buf[4]:
             raise Exception("checksum error")
     ```
     - **Explanation**: This method reads raw data from the DHT sensor into a buffer and performs a checksum validation to ensure the data is accurate. If the checksum fails, an error is raised.

   - **Temperature and Humidity Retrieval:**
     ```python
     def temperature(self):
         return self.buf[2]
     
     def humidity(self):
         return self.buf[0]
     ```
     - **Explanation**: These methods extract and return the temperature and humidity values from the buffer. The `DHT11` class is designed to work specifically with the DHT11 sensor, providing the necessary methods to obtain accurate readings.
    
**Script running in the Termux app in the mobile phone to send data to Adafruit**

This script monitors the log file on the phone for activity data sent from the Raspberry Pi Pico. It processes this data and sends it to Adafruit IO, where it is stored in designated feeds. The script runs continuously, ensuring that all activity data (water intake, exercise, work time) is logged and transmitted in real-time.

**Core Functionalities:**

1. **Adafruit IO Setup:**
   ```python
   AIO_KEY = '#########################'
   AIO_USERNAME = 'Nohemy'
   FEED_NAME_WATER = 'glasses-of-water'
   FEED_NAME_EXERCISE = 'exercise-status'
   FEED_NAME_WORK = 'working-time'

   AIO_URL_WATER = f'https://io.adafruit.com/api/v2/{AIO_USERNAME}/feeds/{FEED_NAME_WATER}/data'
   AIO_URL_EXERCISE = f'https://io.adafruit.com/api/v2/{AIO_USERNAME}/feeds/{FEED_NAME_EXERCISE}/data'
   AIO_URL_WORK = f'https://io.adafruit.com/api/v2/{AIO_USERNAME}/feeds/{FEED_NAME_WORK}/data'
   ```
   - **Explanation**: These lines set up the necessary credentials and URLs for sending data to Adafruit IO. Each feed (water intake, exercise status, work time) has a corresponding URL that the script uses to post data.

2. **Sending Data to Adafruit IO:**
   ```python
   def send_to_adafruit(feed_url, value):
       headers = {
           'X-AIO-Key': AIO_KEY,
           'Content-Type': 'application/json'
       }
       data = {
           'value': value
       }
       print(f'Sending data to {feed_url}: {data}')
       try:
           response = requests.post(feed_url, json=data, headers=headers)
           if response.status_code == 200:
               print('Data sent to Adafruit IO successfully.')
           else:
               print('Failed to send data to Adafruit IO:', response.text)
       except requests.ConnectionError as e:
           print('Connection Error:', e)
       except requests.Timeout as e:
           print('Timeout Error:', e)
       except requests.RequestException as e:
           print('Request Exception:', e)
   ```
   - **Explanation**: This function handles the transmission of data to Adafruit IO. It constructs a JSON payload with the activity data and sends it to the specified feed URL using an HTTP POST request. The function includes error handling to manage potential issues like connection errors or timeouts.

3. **Monitoring Log Files:**
   ```python
   def tail_log_file(file_path):
       global last_processed_line
       with open(file_path, 'r') as file:
           file.seek(0, os.SEEK_END)
           while True:
               line = file.readline().strip()
               if not line:
                   time.sleep(0.1)  # Wait for new data to be written
                   continue
               if line != last_processed_line:  # Avoid processing the same line again
                   process_log_line(line)
                   last_processed_line = line
   ```
   - **Explanation**: This function continuously monitors the specified log file for new lines of data. It ensures that each line is processed only once, avoiding duplicate entries. The function is designed to run indefinitely, updating the Adafruit IO feeds in real-time as new data is logged.

4. **Processing Log Entries:**
   ```python
   def process_log_line(line):
       if "drank_water" in line:
           send_to_adafruit(AIO_URL_WATER, 1)
       elif "exercise_done" in line:
           send_to_adafruit(AIO_URL_EXERCISE, "yes")
       elif "stopped_working" in line:
           match = re.search(r'value":\s*([\d.]+)', line)
           if match:
               working_time = match.group(1)
               send_to_adafruit(AIO_URL_WORK, working_time)
           else:
               print("Error: Could not find a valid numeric value in the log line.")
   ```
   - **Explanation**: This function identifies the type of activity logged (e.g., water intake, exercise, work session) and extracts the relevant data from the log line. It then calls `send_to_adafruit` to transmit the data to the appropriate Adafruit IO feed. For example, if the log indicates that water was consumed, it updates the "glasses-of-water" feed with the value `1`.

5. **Finding the Latest Log File:**
   ```python
   def find_latest_log_file(directory_path):
       log_files = [os.path.join(directory_path, f) for f in os.listdir(directory_path) if os.path.isfile(os.path.join(directory_path, f))]
       if not log_files:
           return None
       return max(log_files, key=os.path.getmtime)
   ```
   - **Explanation**: This function searches the specified directory for the most recently modified log file. This is useful for ensuring that the script monitors the correct file, especially if new log files are generated periodically.

6. **Main Execution:**
   ```python
   if __name__ == "__main__":
       log_file = find_latest_log_file(log_directory_path)
       if log_file:
           print(f"Monitoring log file: {log_file}")
           tail_log_file(log_file)
       else:
           print("No log file found. Please ensure logs are being written to the specified directory.")
   ```
   - **Explanation**: This is the main entry point of the script. It identifies the most recent log file and begins monitoring it for new data. If no log file is found, it prompts the user to check the logging setup.

**Presenting the data**

In Adafruit IO, it's possible to create customizable dashboards that display data from different feeds in real-time. For this project, I built a dashboard consisting of three blocks, each corresponding to one of the key metrics tracked by the device: water intake, exercise status, and work time.

![image](https://github.com/user-attachments/assets/37e44870-9f6c-4660-ac6a-c3b27d2496f2)


**Final Thoughts**

I thoroughly enjoyed working on this project and am excited about the potential to further develop this idea. However, I recognize that my current knowledge is still limited, and there are several areas where the device can be refined and made more robust.

In the future, I plan to integrate a real-time clock module with the Pico to ensure the device always has accurate time, which will improve the reliability of time-based reminders. Additionally, the programs need to be optimized to provide more accurate and clean data, which will enhance the overall user experience.

One significant challenge I encountered was the limited customization options available in Adafruit IO. The platform offers very basic charting and aggregation features, which made it difficult to find suitable visualizations for my data. For future iterations, I recommend exploring alternative platforms that offer more advanced data visualization and customization options.

Overall, this project has been a valuable learning experience, and I look forward to continuing to develop and improve upon it.



