Python-Stackato
===============

A wrapper to the Stackato Client API. Allows users to make requests to the Stackato API. Easy Peasy Lemon Squeezy.

## Usage

### Logging into the client

    from stackato.interfaces import StackatoInterface

    sti = StackatoInterface("https://api.stackato-xxxx.local", "username", "password")
    sti.login()

### Storing the authentication token locally, and deleting an app

    from stackato.interfaces import StackatoInterface

    # Spot the difference!
    sti = StackatoInterface("https://api.stackato-xxxx.local", "username", "password", store_token=True)
    
    if sti.login():
        sti.delete_app('demo')

### Forcing your app to increase its number of instances by one

    from stackato.interfaces import StackatoInterface

    sti = StackatoInterface("https://api.stackato-xxxx.local", "username", "password")

    if sti.login():
        app = sti.get_app('demo')
        app['instances'] += 1
        
        # make a PUT request to the application
        if sti.put_app('demo', app):
            print('added one more instance to this application.')
