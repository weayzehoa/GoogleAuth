1. Install Laravel 6.x LTS with Authentication
    composer create-project --prefer-dist laravel/laravel facebookAuth "6.*"
    composer require laravel/ui "^1.0" --dev
    php artisan ui vue --auth
    npm install && npm run dev
