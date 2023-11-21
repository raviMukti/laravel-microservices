# Laravel Micro Services

You can find the slides in this [link](https://docs.google.com/presentation/d/1cFIrFvHSPFOuZU33WBFsvw0w5KCuGcTe5IOsbS-r-As/edit?usp=sharing)

## Clone this project
```
git clone --recursive https://github.com/raviMukti/laravel-microservices.git <your-prefer-project-name>
```

1. Monolith
    - How it works
        1. cd `/path-to-project/monolith`
        2. Run `composer install`
        3. Run `php artisan migrate`
        4. Run `php artisan serve`
        5. Try make request using postman collection

2. Micro Services
    - How it works
        1. cd to `/path-to-project/rabbitmq` and run `docker-compose up -d` to run rabbitmq container
        2. cd to `/path-to-project/mailhog` and run `docker-compose up -d` to run mailhog container
        3. Open rabbitmq server in `localhost:5672` and login using (User guest, Password guest)
        4. Create exchange
            - OrderExchange : direct
            - StatusExchange : direct
            - NotifyExchange : fanout
        5. Create Queue
            - order_new
            - status_confirm
            - status_pickup
            - notify_confirm
            - notify_pickup
        6. Create Routing-Key
            - order.new (OrderExchange route to order_new)
            - status.confirm (StatusExchange route to status_confirm)
            - status.pickup (StatusExchange route to status_pickup)
        7. cd `/path-to-project/{domain}-service` exp. order-service/delivery-service/notification-service
            - Run `composer install`
            - Run `php artisan migrate`
            - Run `php artisan serve`
            - Try make request using postman collection
