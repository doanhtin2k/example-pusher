# example-pusher
+ server side
    install pusher: composer require pusher/pusher-php-server
+ client side
    npm install --save laravel-echo pusher-js


+ cau hinh file env 
    BROADCAST_DRIVER=pusher
    PUSHER_APP_ID=xxxxxxx
    PUSHER_APP_KEY=xxxxxxx
    PUSHER_APP_SECRET=xxxxxxxxx
    PUSHER_APP_CLUSTER=xxx
+ boostrap.js
    import Echo from 'laravel-echo';

    import Pusher from 'pusher-js';
    window.Pusher = Pusher;

    window.Echo = new Echo({
        broadcaster: 'pusher',
        key: "xxxxxxxxxxxxxx",
        cluster: "xxx",
        forceTLS: true
    });
 + example client 
    Echo.channel("channel-name").listen("DemoEvent", e => {
                console.log('Event listen Demo');
                console.log(e.message);
                this.messages.push(e.message);
                this.$toast.success(e.message, {
                    position: 'top-right'
                })

            });
