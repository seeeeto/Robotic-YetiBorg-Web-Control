# Robotic-YetiBorg-Web-Control
My Robotic Project - YetiBorg Web Control

The original source code is available from the link below;
https://www.piborg.org/blog/yetiborg-v2-examples-web-ui

There were minor issues to be addressed in the original source code and the power comsumption;

#The reverse issue
When you click on Reverse, the wheels don't reverse.
The problems what I found were mainly coding of yeti2Web.py:

1. Line 220 to 225, take off "-" from "drive..." and  * maxPower.
            driveLeft *= maxPower
            driveRight *= maxPower
            ZB.SetMotor1(-driveRight * maxPower) # Rear right
            ZB.SetMotor2(-driveRight * maxPower) # Front right
            ZB.SetMotor3(-driveLeft  * maxPower) # Front left
            ZB.SetMotor4(-driveLeft  * maxPower) # Rear left

2. Change the parameter of each ""Drive( )"" to match each wired wheel. 1 is FWD, 0 is stop, -1 is REV.
            httpText += '<button onclick=""Drive(-1,1)"" style=""width:200px;height:100px;""><b>Spin Left</b></button>\n'
            httpText += '<button onclick=""Drive(1,1)"" style=""width:200px;height:100px;""><b>Forward</b></button>\n'
            httpText += '<button onclick=""Drive(1,-1)"" style=""width:200px;height:100px;""><b>Spin Right</b></button>\n'
            httpText += '<br /><br />\n'
            httpText += '<button onclick=""Drive(0,1)"" style=""width:200px;height:100px;""><b>Turn Left</b></button>\n'
            httpText += '<button onclick=""Drive(-1,-1)"" style=""width:200px;height:100px;""><b>Reverse</b></button>\n'
            httpText += '<button onclick=""Drive(1,0)"" style=""width:200px;height:100px;""><b>Turn Right</b></button>\n'"
            
#The issue with the battery insufficiency
Connecting the ZeroBorg to a 9V battery will only provide < 15 mins of flight so I am seeking another options. I see some alternative options:

Use a 7.4V Li-Po power pack to power everything via the ZeroBorg
Use a 5V mobile power bank. I think then the pack would need to power the ZeroBorg and PiZero => It was the cheapest yet a most effective option available in the Internet.
