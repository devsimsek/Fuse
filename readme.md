# Fuse, The View Engine

Fuse is a fast, secure, and reliable view engine for the SDF framework. It supports various control structures such
as `for`, `foreach`, `while`, `if`, and variable declarations within themes.

## Installation

To install Fuse, you can clone the repository using git:

```shell
git clone https://github.com/devsimsek/Fuse
```

## Usage

Here is an example of how to use Fuse in your PHP project:

1. Include the `Fuse.php` file in your controller or handler:

```php
// Controller/handler file
require "Fuse.php";
```

2. Create a new `Fuse` instance:

```php
$fuse = new \SDF\Fuse();
```

3. Pass data to the view using the `with()` method. You can use this method to add key-value pairs or an object:

```php
$fuse->with('view_engine', 'fuse')->with('title', 'Fuse, The View Engine')->render('example');
```

4. Create the view file (example.php in this case) with the following content:

```php
<html>
<head>
    <title>{{ $title }}</title>
</head>
<body>
    Powered by {{ $view_engine }}
</body>
</html>
```

## Documentation

Fuse provides a simple and efficient template rendering mechanism. It allows you to pass data to your view files using
the `with()` method and render the content with the `render()` method.

### Methods

#### `withObject(mixed $data): self`

The `withObject()` method allows you to add an object to the data array. The data passed through this method will be
merged with the existing data.

Parameters:

- `$data`: The object to add to the data array.

Returns:

- `self`: Returns the current instance of the Fuse object.

#### `with(string $key, mixed $value): self`

The `with()` method allows you to add a key-value pair to the data array.

Parameters:

- `$key`: The key.
- `$value`: The value.

Returns:

- `self`: Returns the current instance of the Fuse object.

#### `render(string $view, string|null $directory = null): string|bool`

The `render()` method is used to render the view file with the provided data.

Parameters:

- `$view`: The path to the view file.
- `$directory`: The base directory for the view file (optional).

Returns:

- `string|bool`: Returns the rendered content of the view file as a string or `false` if the file is not found.

### Template Syntax

Fuse supports several template syntax features that enable you to control the rendering of your views effectively:

#### Conditional Statements

- You can use `@if`, `@elseif`, and `@else` directives for conditional statements.

```php
@if ($condition)
    // Content to render if the condition is true.
@elseif ($another_condition)
    // Content to render if the second condition is true.
@else
    // Content to render if none of the conditions are true.
@endif
```

#### Loops

- For loops using `@for`:

```php
@for ($i = 0; $i < 5; $i++)
    // Content to render for each iteration.
@endfor
```

- ForEach loops using `@foreach`:

```php
@foreach ($array as $item)
    // Content to render for each item in the array.
@endforeach
```

- While loops using `@while`:

```php
@while ($condition)
    // Content to render while the condition is true.
@endwhile
```

#### Variable Declarations

- You can declare variables using the `@var` directive:

```php
@var $variable_name = 'Value';
```

#### Variable Output

- You can output variables using the `{{ $variable }}` syntax. Fuse automatically escapes the output to prevent XSS
  attacks.

```php
{{ $title }}
```

If you want to output a variable without escaping, use the following syntax:

```php
{{ $variable_name }}
```

## Contributors

- [devsimsek](https://github.com/devsimsek) - Developer and maintainer

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Todo

- Section and extend support.

Please make sure to refer to the [GitHub repository](https://github.com/devsimsek/Fuse) for the latest updates, bug
reports, and feature requests.

---

This project is licensed under the MIT License. See the [LICENSE](https://devsimsek.mit-license.org) file for details.
