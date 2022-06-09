# Temperature-Control-System-using-Labview
# Main Front Panel 
![image](https://user-images.githubusercontent.com/51925070/172768249-8a97e4b3-90c9-45b8-8bce-fe5efd9611af.png)

(Figure 1.1 Front Panel: Temperature Control System)

The main functional areas of the interface include the user input area, data record and result display area. The LED labelled with "Card Status" indicates whether the I/O hardware is connected to the computer. The real-time temperature of the process and the speed of the fan is displayed in a panel-style indicator as well as recorded on a rolling chart graph. By showing both set temperature and measured values on the graph, we can easily see how the control system responds to the setpoint changes. This would be helpful when the user tries to modify the default parameters (obtained through the Zeigler-Nichols closed-loop tuning method) of the PI controller in the numerical control boxes to achieve the desired system performance. The numerical control underneath the PI values box sets the sampling rate, which controls the execution speed of the control system. There is a push-button above the PI gains box allowing the operator to switch between manual and automatic control. The slider allows one to manually control the fan speed.
When the "Save” button is pressed, the system will record the real-time temperature and set temperature within the time period set by the user to a file. By default, the recording time period(Time Targets) is 300 seconds. The progress bar just below will show the progress of recording." Set Temperature History” area displays the set history from an operation logging file.

 # Block Diagram and its Function
 
 ![image](https://user-images.githubusercontent.com/51925070/172768357-39f85fe0-827d-4fe8-9e57-69cc6fddf3db.png)

(Figure 2.1 Screenshot of LabView Block Diagram)

![image](https://user-images.githubusercontent.com/51925070/172768407-d02f0c69-2510-48cb-ad7e-20ae5d60acb3.png)

(Figure 2.2.1 Block Diagram of the Temperature Control System)

![image](https://user-images.githubusercontent.com/51925070/172768438-12ec977f-34d7-47ea-af05-dc7eba1236e8.png)

(Figure 2.2.2 Screenshot of Control Part of LabView Block Diagram)

When the set temperature and measured temperature do not match, an error is produced. The PI controller will modify the manipulated variable(duty cycle) to try and get the temperature of the heated resistor to match the set temperature. Since the fan is controlled by the pulse width modulation(PWM) method, the fan speed changes correspondingly with the duty cycle between 0 and 100%. Hence the saturation block is used to keep the output from the PI controller within legal values(0-100).

Once the “Save” button in the front panel is pressed, the real-time measured temperature data and the set temperature data are allowed to flow inside the file saving loop through the channels. The data will keep written into the Excel file until the recording time elapsed.

![image](https://user-images.githubusercontent.com/51925070/172768733-1e13d6d9-8ecb-441a-b043-7c1e7ea546ac.png)

(Figure 2.3.1 Saving Record File)
An event structure is created to detect the value change in the set temperature control box. Once the value changes, it will be written into an operation log file along with the date and time.

![image](https://user-images.githubusercontent.com/51925070/172768746-65558c64-f081-403c-b60b-ba35164869f0.png)

(Figure 2.3.2 Saving Operation LogFile )

