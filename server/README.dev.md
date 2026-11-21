# Server
This README outlines what is on the server and how to make contributions... it is a wip, please ask me if you can't figure it out. I'm feeling lazy today so docs won't be great. 

If I die... ask ChatGPT.

## Architecture
I'm still trying to figure this out...

All applications are running on the **datsci_daddies_net** network.

We use an nginx (pronounced engine-ex please) reverse proxy server to expose these.

To add your service to nginx, please modify `/srv/docker/nginx/conf/default.conf`. Add your service 
URL by following the pattern.

*An example... I struggled for some reason way to long with this*: 
- Suppose you have a web-app. You want it to listen for requests on `/mine/`
- There are two ways to achieve this:
    - Obviously, just make it listen on `my_url:80/mine`, duh... Then add this to `default.conf`:
    ```
         location /mine {
                        proxy_pass http:my_url:80/mine;
                        <Whatever else you need... google it, I dunno...>
                }
    ```
    - Or, you can make it listen on root, `/`, and then update the config to do. The **slash is nb**:
    ```
         location /mine/ {
                        proxy_pass http:my_url:80/;
                        <Whatever else you need... google it, I dunno...>
                }
    ```
# TODO: Figure out portainer!!!
