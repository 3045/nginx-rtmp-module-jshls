# NGINX RTMP module - JS HLS

## What and why?

### What?

This module when installed into the working directory as the previous module (found in ``/usr/share/nginx/modules`` after executing ``apt install -y nginx libnginx-mod-rtmp``) will work identically to all other copies of this module.

### Why?

CDN providers like Cloudflare will advertise commonly accessed files, such as JavaScript files, when requested. After the first time it has been requested, the JavaScript file is generally stored in their global edge cache, so further requests never make it to the origin, meaning less work for the origin.

This module uses the same idea; since Cloudflare does not cache .ts files intentionally (since you're technically not supposed to stream over Cloudflare) we will instead serve the exact same files to users, except with a .js extension. This results in the live media being cached and therefore meaning less load on the origin server. Using this setup, we are able to achieve a caching rate of over 99.5% when delivering livestream media, delivering the same media to thousands of more users whilst using less resources on the origin.

### How? Where's the source code...?

I edited this module in less than a few minutes using HxD. It is so easy to do, you can do it yourself. This is obviously the wrong way to do it; the correct way is to fork the repository of the original project, edit the code, compile it, test it and if it works publish the code (and perhaps the prebuilt module too) but I did not want to compile it in the first instance and have to deal with all the issues that comes along with it, so this works for now.

If someone is willing to do the work for me, please be my guest but this works for now and I am happy with it.
