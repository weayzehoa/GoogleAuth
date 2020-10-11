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
5. 取得 Google OAhth 資料並增加到 .env 設定中
    GOOGLE_CLIENT_ID=XXXXXXXXXXXXXXXXXXXXXXXXXXX
    GOOGLE_CLIENT_SECRET=XXXXXXXXXXXXXXXXXXXXXXX
    GOOGLE_REDIRECT=https://localhost/callback
6. 建立 SocialAuthGoogleController 控制器
    php artisan make:controller SocialAuthGoogleController
7. 修改 route/web.php 新增
    Route::get('/redirect', 'SocialAuthGoogleController@redirect');
    Route::get('/callback', 'SocialAuthGoogleController@callback');
8. 建立 Model 及 修改相關檔案
    php artisan make:model SocialGoogleAccount -m
    a. 修改 app/SocialGoogleAccount.php
    b. 修改 database/migrations/2020_10_11_030936_create_social_google_accounts_table.php
    c. 修改完成後執行 php artisan migrate:refresh
9. 新增 app/Services 目錄及 SocialGoogleAccountService.php 並修改它
10. 修改 login 視圖，新增一個按鈕
11. 測試，完成。
