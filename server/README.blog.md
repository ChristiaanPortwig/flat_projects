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

I went with vaultwarden, because... shocker, that's what the tutorial recommended. 

Due to my eduroam issue, I can't directly pull images from the internet to my pi. So I have to pull 
it on my (Intel, important for later) laptop and transfer it to the pi using portainer. When doing 
this, the images wouldn't work. After inspecting the logs (like a caveman who hasn't heard about 
generative AI), I saw that I was getting an "exec format error". After googling, I stumbled across 
[this](https://stackoverflow.com/questions/73285601/docker-exec-usr-bin-sh-exec-format-error) 
stackoverflow page, pulled the arm image, and it worked!

The tutorial wanted me to use nginx, and who am I to argue. I'm like 80% certain what this does, 
will have to watch another Youtube video about it. Anyways, I did the following:
- Generate a self-signed ssl certificate using openssl
- Create a nginx config file
- Create a new "stack" (like a docker compose) for the nginx server, running on the vaultwarden 
network.
-Allowing me to connect to vaultwarden on my local network!!!


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
