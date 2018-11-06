# Halloween-Hue

Bash scripts for halloween hue effects 



This Git repo contains the 4 bash scripts I used to create some halloween effects, as detailed at https://willow.systems/iot-halloween/

Three of the bash scripts (lightningStrike, dim and flicker) take the hue bulb ID as an argument, and cause the effect. The fourth script 'Halloween' randomly calls the other three with random light IDs. If you want to use the 'halloween' script for yourself, you will want to update the light IDs in it

## Setup

Setup is pretty straightforward, you just need to know the hue hub IP Address. The best place to find this is your router logs. 

### Install prereqs

The only prerequisit is curl, which is likely included in your distro. If not, install via your package manager.

### Get HUE username/token.

To get a hue username (which is your access token), press the hue button on the hub then issue the command: 


`curl -s -X POST -d '{"devicetype":"halloween_script"}' http://<your hue IP address>/api >user.txt`


where <your hue IP address> is the IP address of your hue hub.

You should now have a file called user.txt containing a string similar to '1028d66426293e821ecfd9ef1a0731df'. To check, run 

`cat user.txt`

### Update the IPs

Now that you have the user.txt file in the same directory as the scripts, the final steps in each script is to edit the line:

`URL=""`

to contain your HUE Hub IP address. E.g.

`URL="192.168.1.24"`

## Running the scripts

To run the effect scripts, call them with the following arguments:

`./{script} <light ID> <turn on afterwards (optional)>`

where `<light ID>` is the ID of the light and `<turn on afterwards (optional)>` is an optional argument specifying whether the light should remain off or return to dim white afterwards.

## Examples

`./dim 8` - Dim bulb 8 and stay off aftewards

`./flicker 3 true` - Flicker bulb 7 and then stay on

`./lightningStrike 4` - Perform the lightning effect on bulb 4 and turn off






