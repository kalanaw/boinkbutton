# boinkbutton
Simple IoT button to get things done

Super simple IoT button to trigger an event (IFTTT webhook over HTTP GET in this case). 
MCU used in ESP8266wifi (NodeMCU devkit v2) with NodeMCU firmware with modules `file, gpio, net, node, tmr, uart, wifi`.

The implementation has an `init.lua` that will start the app with board booting up. After around 15 seconds it listens with button click via gpio (D1) and sends a request to ifttt predefined endpoint. Button clicks are debounced and there is a *poorly implemented* delay between network requests to keep things sane.

### Installation

 - Ensure your board is running correct firmware with required modules. 
 - Enter your wifi SSD and password to `credentials.lua`.
 - Enter your IFTTT webook Maker Key to `keys.lua`.
 - Upload all the lua files to your board.
 - Restart the board. init.lua would run at bootup.
 
 ### Troubleshooting
 
 - **Board freezes after bootup?** `init.lua` has a delay function after it initializes wifi. This gives you a 10 seconds window to delete or rename the `init.lua` file. Application startup sequence checks if the `init.lua` file exists before invoking `application.lua` which probably has an error to freeze up your execution.
