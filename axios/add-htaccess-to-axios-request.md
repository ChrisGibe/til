# Add a htaccess to your axios request

If you have a wesite who have an htaccess security, you can add the "Authentification" with the login and password directly inside your axios request.
Axios can take it as a second parameter, inside an object.

Here's an example :

```
axio.get("https://myurl.com/mydata.json", {
    auth: {
        username: 'myLogin',
        password: 'myPassword'
    };
});
```