<h1> DuinoEthernet </h1>
  <p>Forked from duino but with Arduino's Ethernet power!</p><br />
<img src="http://forthebadge.com/images/badges/built-with-love.svg"/>

<h2>Usage</h2>
  <p>This basically transforms your Arduino into a simple (not that robust) REST server. You can interact with
 Arduino via instantly if you simply connect it to the network. The basic idea behind this simple code is to
 control Arduino sending simple HTTP post requests with JSON as content.</p>
 <p>Right now I've only implemented 4 things (if you have time and are a awesome person fell free to 
 contribute with whatever you can):</p>
 <ul>
  <li>Analog Digital</li>
  <li>Analog Read</li>
  <li>Digital Read</li>
  <li>Digital Digital</li>
 </ul>
 
<h3>Crème de la Crème : How to send messages to Arduino?</h3>
 <p>In a basic JSON object (as described in <a href="http://jsonapi.org/format/">here</a> 
 you'll need to put 3 basic stuff for this to work: command, pin and value. <br /> 
 As explained <a href="http://jsonapi.org/format/">here</a> since they are integers, you dont need to put 
 "" arround the value, so don't put them</p>
 
 <h4>Table of commands and desired behavior</h4>
 
 <table style="width:100%">
 <tr>
    <td><strong>Command</strong></td>
    <td><strong>Type</strong></td>
    <td><strong>Behavior<strong></td>
  </tr>
  <tr>
    <td>1</td>
    <td>Digital write</td>
    <td>Digital write, change the value of the pin depending on the value that you send it</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Digital Read</td> 
    <td>Will read either 1 or 0 on the desired pin and return the result</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Analog Write</td> 
    <td>Will only work on PWM pins, change the value of the output in that pin it can go from 0 to 255</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Analog Read</td> 
    <td>Reads the value from the A1, A2.. pins (whenever you want to read this don't write pin as A1, write it as
    1, 2, 3 ... etc)</td>
  </tr>
</table>
 <p>Note: 1, 2, 3 commands only work for digital pins, command 4 will read analog input from the pins labeled A1, A2 ...</p>
 <p>A simple example of turning on a LED could be written as (it could be like that or with new lines in between):</br>
 </p><code>
  {
    "command" : 1,
    "pin" : 13,
    "value" : 1
  }
 </code>
 <h4>Response</h>
 <p>There will be always a resoponse from the server as (JSON encoded) that will have the result that could be
 either true or false, the pin number that was modified, and the value that was read read or if it wrote something 
 on a pin it will return that value</p>
 <p>A response to a request such as the one shown above will look like:</p>
 </p><code>
  {
    "result" : "true",
    "pin" : 13,
    "value" : 1
  }
 </code>
 
 <h2>Licence</h2>
 The MIT License (MIT)

Copyright (c) <year> <copyright holders>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
