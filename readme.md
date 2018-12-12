# Emoncms Remote Access

Background discussion: [https://community.openenergymonitor.org/t/emoncms-local-vs-remote/7268](https://community.openenergymonitor.org/t/emoncms-local-vs-remote/7268)

## Login on mqtt.emoncms.org

Login on mqtt.emoncms.org with your emoncms.org username and password to register for the remote access service.

https://mqtt.emoncms.org

## Client Installation

Install python dependencies:

    pip install python-dotenv

Install and start remoteaccess service:

    sudo ln -s /home/pi/remoteaccess/remoteaccess.service /lib/systemd/system
    sudo systemctl enable remoteaccess.service
    sudo systemctl start remoteaccess
    
View service log:

    journalctl -f -u remoteaccess -n 100

Create .env settings file with emoncms.org username and password.

    cp .env.example .env
    nano .env

Enter your local emoncms apikey and remote emoncms.org account username and password to connect:

    # application mode
    APP_ENV='production'
    # emoncms api write key
    EMONCMS_APIKEY='apikey'
    # mqtt broker connection
    MQTT_HOST='mqtt.emoncms.org'
    MQTT_USERNAME='username'
    MQTT_PASSWORD='password'
    MQTT_PORT=8883
    MQTT_TLS=true

    # Save As .env for production
    # Save As .env.dev for development