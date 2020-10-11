1. Install Laravel 6.x LTS with Authentication
    composer create-project --prefer-dist laravel/laravel facebookAuth "6.*"
    composer require laravel/ui "^1.0" --dev
    php artisan ui vue --auth
    npm install && npm run dev
2. Install Laravel/Socailtie
3. 修改 config/app.php
    a. providers區段加入
        Laravel\Socialite\SocialiteServiceProvider::class,
    b. aliases區段加入
        'Socialite' => Laravel\Socialite\Facades\Socialite::class,
4. 修改 config/services.php，加入 Google
    'google' => [
        'client_id' => env('GOOGLE_CLIENT_ID'),
        'client_secret' => env('GOOGLE_CLIENT_SECRET'),
        'redirect' => env('GOOGLE_REDIRECT'),
    ],
