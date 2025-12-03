# Default Page Handler Extension

The default page handler for the PyroCMS Pages module.

## Description

This extension provides the standard page rendering handler for the Pages module in PyroCMS. It handles the complete lifecycle of page requests including authorization, breadcrumb generation, content loading, and response generation.

## Features

- **Authorization**: Checks page access permissions before rendering
- **Breadcrumb Generation**: Automatically creates navigation breadcrumbs
- **Content Loading**: Loads page content and related data
- **Response Handling**: Generates appropriate HTTP responses
- **Extensible**: Serves as the base handler that other page handlers can extend

## How It Works

When a page is requested, the default handler executes the following workflow:

1. **Authorization** - Verifies user has permission to view the page
2. **Breadcrumbs** - Builds breadcrumb navigation trail
3. **Loading** - Loads page content and metadata
4. **Content** - Processes and prepares page content
5. **Response** - Generates the HTTP response with rendered content

## Usage

This handler is automatically used by default for all pages in the Pages module. No configuration is required.

### Using in Page Types

When creating a page in the PyroCMS control panel, this handler is the default selection:

1. Navigate to Pages in the control panel
2. Create or edit a page
3. The "Default" handler is automatically selected

### Custom Handlers

You can create custom page handlers that extend or replace this default behavior:

```php
<?php namespace Acme\CustomPageHandlerExtension;

use Anomaly\PagesModule\Page\Handler\PageHandlerExtension;
use Anomaly\PagesModule\Page\Contract\PageInterface;

class CustomPageHandlerExtension extends PageHandlerExtension
{
    protected $provides = 'acme.extension.custom_page_handler';
    
    public function make(PageInterface $page)
    {
        // Your custom page handling logic
    }
}
```

## What It Handles

### Authorization
Ensures the current user has permission to access the page based on:
- Page visibility settings
- User roles and permissions
- Authentication requirements

### Breadcrumbs
Generates breadcrumb navigation showing:
- Page hierarchy
- Current page location
- Parent page links

### Content Processing
- Loads page content from database
- Processes page fields
- Prepares view data
- Handles page metadata

### Response Generation
- Renders page template
- Sets HTTP headers
- Returns appropriate response type
- Handles redirects if configured

## Requirements

- PyroCMS 3.x
- Anomaly Streams Platform ^1.8
- Anomaly Pages Module

## When to Use

The default handler is suitable for:
- Standard content pages
- Basic informational pages
- Documentation pages
- About/Contact pages
- Any page requiring standard rendering

## When to Create a Custom Handler

Consider creating a custom handler for:
- Complex interactive pages
- Pages requiring special data loading
- Custom response formats (JSON, XML, etc.)
- Pages with unique authorization logic
- Forms or application-specific functionality

## Integration

This extension integrates seamlessly with:
- **Pages Module** - Provides default page rendering
- **Streams Platform** - Utilizes streams for content management
- **Template System** - Renders views using Twig/Blade
- **Authorization System** - Enforces access control

## Support

- **Email**: support@pyrocms.com
- **Website**: http://pyrocms.com/
- **Documentation**: [PyroCMS Documentation](https://pyrocms.com/documentation)

## License

This extension is open-sourced software licensed under the [MIT license](LICENSE.md).

## Authors

- **PyroCMS, Inc.** - [Website](http://pyrocms.com/) - support@pyrocms.com
