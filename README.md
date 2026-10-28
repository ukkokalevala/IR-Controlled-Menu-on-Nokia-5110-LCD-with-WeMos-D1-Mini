IR-Controlled Menu on Nokia 5110 LCD
IR-Controlled Menu on Nokia 5110 LCD — WeMos D1 Mini

Build a two-page menu navigated entirely by IR remote. Controls an LED: on, off, blink slow, blink fast. Includes cursor navigation, page flipping, direct 1–9 item selection, live blink-speed adjust, contrast cycling, and repeat-frame filtering.

Critical Wiring Note
Connect the IR receiver to D4 or D5 — NOT D0.
GPIO16 (D0) has no interrupt support and the IR library will silently fail to decode. This is the #1 reason this project appears "broken."

Wiring
Nokia 5110 LCD

LCD Pin	WeMos D1 Mini
RST	D2
CE / CS	D1
DC	D6
DIN / MOSI	D7
CLK / SCK	D5
VCC	3.3V only
GND	GND
BL	3.3V (or via 330Ω)
IR Receiver

IR Pin	WeMos D1 Mini
OUT	D4 (not D0)
VCC	3.3V
GND	GND
LED

LED	WeMos D1 Mini
+ (via 220Ω)	D8
−	GND
Controls
Button	Action
▲ ▼	Move cursor
◀◀ ▶▶	Page back / forward
▶ Play	Select / activate
■ Stop	Back / reset
EQ	Cycle LCD contrast
ST/Rept	Toggle repeat mode
VOL+ / VOL−	Adjust blink speed
1–9	Direct item select
Libraries
IRremoteESP8266 — IR decoding (tested v2.8.6)

Adafruit GFX Library — graphics primitives

Adafruit PCD8544 Nokia 5110 LCD Library — display driver

All available in the Arduino Library Manager.

Key Features
Two-page menu — LED control + settings

Non-blocking blink — menu stays responsive while LED blinks

Repeat-frame filtering — held buttons don't glitch the menu

Direct 1–9 selection — jump to any item instantly

Live value adjust — change blink speed with VOL+/−

Contrast cycling — EQ button adapts to your display

Fixed LCD layout — 6 rows at 8-pixel spacing, no overlap

About Remote Range
NEC remotes send long, well-defined frames and work from across the room. Non-standard remotes (often decoded as UNKNOWN) send shorter or irregular frames and may need to be held close to the receiver. This is a property of the remote's IR LED and protocol — not a bug in the code.

Tip: If range is poor, try fresh batteries in the remote, or add a 100Ω resistor + 100µF capacitor to the receiver's VCC for better noise immunity.

Serial Monitor
Set to 9600 baud. The sketch prints each received code as RX=0x00FF30CF for debugging.

What's Next
Save LED mode to EEPROM across reboots

Add a third page for brightness (PWM)

Turn SHOW CODES into a live IR viewer

Build a learn mode to capture codes from any remote

