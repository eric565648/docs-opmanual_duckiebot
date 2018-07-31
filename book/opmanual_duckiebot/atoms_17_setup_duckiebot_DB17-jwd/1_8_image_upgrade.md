# Duckiebot Image Upgrade {#sec:duckiebot_image_upgrade status=draft}

<div class='requirements' markdown="1">

Requires: A Duckiebot in configuration `DB17-CO+w`

Requires: An Raspberry Pi3 B+

Result: A Duckiebot with Pi3 B+

</div>

Since there's a new Raspberry Pi3 B+ model, we leveraged the new powerful CPU and the on-board 5GHz network. In this chapter, our goal is to upgrade the old image for Pi3 B to an image that can be used both on B and B+.

You can upgrade the image when you're initializing a Duckiebot, or you can also upgrade your own beloved Duckiebot that you have used for a while.

## Acquire and source upgrade script

If you're interesting to the steps of upgrade, you can look inside the script file.

    duckiebot $ cd
    duckiebot $ wget "https://github.com/duckietown/Software/raw/jquack-devel/Pi_update.sh"
    duckiebot $ sh Pi_update.sh

shutdown your Pi after all processes have finished.

    duckiebot $ sudo shutdown -h now

## Reconnect to the Duckiebot

Remove old RPI3 B from your Duckiebot, installed new RPI3 B+ and insert your SD card. Turn on your Duckiebot, it should automatically connect to a wifi in reach called 'duckietown' with password 'quackquack'.

Try connect to the same wifi and ping your Duckiebot from laptop

    laptop $ ping ![robot name].local

It should response

    PING ![robot name].local (![X.X.X.X]): 56 data bytes
    64 bytes from ![X.X.X.X]: icmp_seq=0 ttl=64 time=2.164 ms
    64 bytes from ![X.X.X.X]: icmp_seq=1 ttl=64 time=2.303 ms
    ![...]

At this point, you finished the upgrade procedure! Congrats!

If it didn't work, make sure there's a wifi called 'duckietown' with password 'quackquack' near by. If it still not working, try connect Duckiebot and your laptop with Ethernet cables under same (wifi) router to make sure they are under same network. At this moment, you DEFINITELY should able to ping your Duckiebot. If not, prey to God, or see if you simply forget to insert the plug of switch of router.

If you successfully ping your Duckiebot, ssh to your bot and add wifi Connection.

    laptop $ ssh ![username]@![robot name].local

In your Duckiebot

    duckiebot $ sudo nmcli dev wifi con "duckietown" password "quackquack"

After this step, use ifconfig to make sure your Duckiebot connect to 'duckietown' wifi.

    duckiebot $ ifconfig
