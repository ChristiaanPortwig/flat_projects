# Server
(By Christiaan)

This is how we actually use our projects. We run a server hosted on a Raspberry pi 3b. This also 
forms the center of the **Centrapine** architecture (hopefully there's some docs about this 
somewhere... basically our plan to only use one or two esp32s and have them offload to the pi).

The remainder of this README will probably be treated more like a blog.

## Server setup

First I had to flash an OS onto the pi. My choice was Pi OS lite... because its what the tutorial 
told me (and it doesn't have a GUI, so more performance for running 1T Parameter models - joke).

This was pretty easy, since I just used the Raspberry Pi imager.

Then I installed docker and portainer directly from the pi.

After I figured out the network stuff, I concluded that it would work to set up a hotspot from my 
laptop and have the pi join it... it worked.




## Password manager
When I initially read the blackdevice tutorial, I thought "eeu", we won't host a password manager...

Then I tried to create a 1Password account to share with my flatmates with the pi's login info, and 
you have to pay, so then I decided that this will be one of our services.

## Resources
- https://www.youtube.com/watch?v=kF0ofY5x5qk
- https://blackdevice.com/turn-a-raspberry-pi-into-a-multi-service-home-server-with-docker-and-portainer/
- https://www.youtube.com/watch?v=a-EIyI4VgJs
- https://blackdevice.com/docker-raspberry-pi-guide/

### AI Usage (Using some OpenAI model)
- Figuring out how to connect the pi to our university wifi network (this was before we moved into 
the flat)... and some more networking shenanigins
- I had a bug where apt wouldn't work... googled it and everything, then my eye accidentally fell 
on AI search: datetime. This prompted me to make sure the time is correct on the pi, it wasn't. 
This fixed the bug. I feel semi satisfied, since I at least tried to do it myself.
