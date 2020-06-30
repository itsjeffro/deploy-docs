# Broadcasting

To allow real-time feedback when a deployment or server connection has started or finished, you may set up the application 
to utlise Laravel's broadcasting feature.

Deploy currently only supports Pusher.

```bash
composer require pusher/pusher-php-server "~4.0"
```

Note: You may need to restart the queue worker to pick up on your configuration updates.

## Configuration

You will need to change your broadcast driver to `pusher` in your `.env` file:

```bash
BROADCAST_DRIVER=pusher
```

Finally, you may update the Pusher credentials. The frontend assets for Deploy will automatically include your Pusher key and cluster.