## Laravel

- Laravel is a widely used PHP framework for building modern, robust web applications.
- It follows the **Model-View-Controller (MVC)** design pattern, emphasizing simplicity, elegance, and developer productivity.

Laravel provides:
- **Elegant Syntax**: Simplifies web development with readable, expressive code.
- **Comprehensive Features**: Includes built-in tools for routing, ORM, templating, authentication, and more.
- **Developer Productivity**: Boosted by tools like Artisan CLI, pre-configured setups, and extensive documentation.

---

## **The MVC Design Pattern in Laravel**

- Laravel is based on the **MVC (Model-View-Controller)** design pattern.
- This pattern separates the application’s data, user interface, and control logic, organizing it into three interconnected components (using php):

  ![MVC Framework](https://media.geeksforgeeks.org/wp-content/uploads/20221109172029/MVCFramework1-660x473.png)


1. **Model**: 
   - Represents data and business logic.
   - Interacts with the database via **Eloquent ORM** (Object-Relational Mapping).
   - Defines relationships, scopes, and attributes for data.
   - Example:
     ```php
      // **Location**: App/Models/A.php
      namespace App\Models;
      
      use Illuminate\Database\Eloquent\Model;
      
      class A extends Model {
          protected $fillable = ['x', 'y'];  
      }

     ```

2. **View**: 
   - Handles the presentation layer where data is displayed to the user.
   - Uses **Blade Templates** for dynamic content and layouts.
   - Example:
     ```blade
     <!-- **Location**: resources/views/abc.blade.php -->
      <h1>All A's</h1>
      @foreach ($data as $item) 
          <h2>{{ $item->x }}</h2>
          <p>{{ $item->y }}</p>
      @endforeach

     ```

3. **Controller**: 
   - Manages application logic and communication between Model and View.
   - Receives HTTP requests, interacts with Models, and returns Views.
   - Example:
     ```php
     // **Location**: App/Http/Controllers/Mac.php
      namespace App\Http\Controllers;
      
      use App\Models\A;  
      use Illuminate\Http\Request;
      
      class Mac extends Controller {  
          public function index() {
              $d = A::all();  
              return view('abc', ['d' => $data]);  
          }
      
          public function store(Request $r) {
              A::create($r->all());  // Using 'A' model
              return redirect('/abc');  // Redirect to the updated route '/abc'
          }
      }

     ```


4. **Routing**:
   - Defines URL endpoints and links them to controllers.
   - Laravel uses routes to link requests to specific controllers and methods.
   - Example:
     ```php
      // **Location**: routes/web.php
      Route::get('/abc', [Mac::class, 'index']);  
      Route::post('/abc', [Mac::class, 'store']);  

     ```
     ### Explanation
       - The Model accesses the database (specified in another file) via Eloquent.
       - Class A inherits Laravel's Model to be the **Model** class of this program.
       - It mass-assigns 'x' and 'y', meaning we can use a single query to edit both, instead of using multiple.<br><br>  
       - The controller program imports the 'A' Model class.
       - The Mac class extends the controller, becoming the **Controller** of the program.
       - The `index()` function accesses all data using `all()` from the Model class A, assigned to `$d`.
         - Then it returns `$d` as `$data` to `abc.blade.php` (view).
       - The `store()` function uses `$r` as a parameter, since it is accessed using POST (in routing).
         - It then creates a new entry in database via Model A, and updates all fillable entries ('x', 'y') using `$r`.
         - After entering the data, it redirects to the view to show the change in view (`abc.blade.php`).<br><br> 
       - The **View** page uses Blade templating, which allows dynamic data in HTML.
       - In the `@foreach` loop, it accesses each element in `$data` passed from *Controller Mac*.
         - The x and y entries of each entry in `$data` is displayed.
         - We can also use Model A to display anything else like id, name, etc. However they cannot be edited, due to them not being in `$fillable`. This ensures security.<br><br>       
       - In **Routing**, the GET method is used to call the `index()` function inside class Mac from the view abc.
       - The POST method is used to call the `store()` function, where the data from POST is sent to the function, and accessed in Controller as `Request $r`.
---



## **Key Features of Laravel**

1. **Routing**: An expressive and simple routing system.
   - Example:
     ```php
     Route::get('/', function () {
         return view('welcome');
     });
     ```

2. **Eloquent ORM**: ORM is a technique that allows developers to interact with a database using an object-oriented approach, rather than writing raw SQL queries.
   - Example:
     ```php
     $post = Post::find(1);
     $post->title = "Updated Title";
     $post->save();
     ```

3. **Blade Templating Engine**: Dynamic templating system for rendering HTML.
   - Features:
     - Layout inheritance:
       ```blade
       <!-- resources/views/layouts/app.blade.php -->
       <html>
       <body>
           @yield('content')
       </body>
       </html>
       ```

       ```blade
       <!-- resources/views/home.blade.php -->
       @extends('layouts.app')

       @section('content')
           <h1>Welcome Home!</h1>
       @endsection
       ```

4. **Middleware**: For filtering HTTP requests (e.g., authentication).
   - Example:
     ```php
     // app/Http/Middleware/CheckAge.php
     public function handle($request, Closure $next) {
         if ($request->age < 18) {
             return redirect('home');
         }
         return $next($request);
     }
     ```

5. **Authentication & Authorization**:
   - Built-in functionality for user authentication and role-based access.

6. **Artisan CLI**:
   - Commands for common tasks like migrations and seeding:
     ```bash
     php artisan make:model Post --migration
     php artisan migrate
     ```

7. **Task Scheduling**:
   - Schedule tasks without external tools like CRON.
     ```php
     // app/Console/Kernel.php
     protected function schedule(Schedule $schedule) {
         $schedule->call(function () {
             DB::table('posts')->delete();
         })->daily();
     }
     ```

---

## **Setting up a Laravel Development Environment**

### 1. **System Requirements**
   - PHP >= 8.0
   - Composer (Dependency Manager)
   - Web Server: Apache/Nginx
   - Database: MySQL/PostgreSQL/SQLite

### 2. **Installation Steps**
1. Install Composer:
   ```bash
   curl -sS https://getcomposer.org/installer | php
   mv composer.phar /usr/local/bin/composer
   ```

2. Create a new Laravel project:
   ```bash
   composer create-project laravel/laravel my-app
   cd my-app
   ```

3. Serve the application:
   ```bash
   php artisan serve
   ```
   Visit [http://localhost:8000](http://localhost:8000).

### 3. **Environment Configuration**
- Modify `.env` file for database and other settings:
  ```env
  DB_CONNECTION=mysql
  DB_HOST=127.0.0.1
  DB_PORT=3306
  DB_DATABASE=laravel
  DB_USERNAME=root
  DB_PASSWORD=secret
  ```

---

## **Application Structure in Laravel**

Laravel’s file structure is designed for simplicity and scalability:

1. **`app/`**: Contains core application logic.
   - **`Models/`**: Eloquent models (e.g., `Post.php`).
   - **`Http/Controllers/`**: Controllers for handling requests.
   - **`Http/Middleware/`**: Middleware for HTTP request filtering.

2. **`resources/`**: Views, language files, and raw assets.
   - **`views/`**: Blade templates (e.g., `posts.blade.php`).

3. **`routes/`**: Application routes.
   - **`web.php`**: For web (HTTP) routes.

4. **`database/`**: Migrations, seeders, and factories for database management.

5. **`public/`**: Web-accessible files (e.g., `index.php`, CSS, JS).

6. **`config/`**: Configuration files (e.g., `app.php`, `database.php`).

---

## **Conclusion**

Laravel provides a modern, efficient framework for building web applications. Its adherence to the MVC design pattern, combined with powerful tools like Eloquent ORM, Blade templating, and Artisan CLI, make it an excellent choice for developers. By setting up a structured environment and understanding the application architecture, you can leverage Laravel to develop scalable, maintainable applications.
