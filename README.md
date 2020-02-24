# heroku-rs

**This project is currently under development**

## Intro

This is a rust wrapper for the [Heroku](https://heroku.com/) [v3 API](https://devcenter.heroku.com/articles/platform-api-reference/).

This is a work in progress mostly as a way to learn Rust.

### Useful links

[Heroku quickstart](https://devcenter.heroku.com/articles/platform-api-quickstart) 

[Heroku API reference](https://devcenter.heroku.com/articles/platform-api-reference)

[Generating a heroku API key](https://help.heroku.com/PBGP6IDE/how-should-i-generate-an-api-key-that-allows-me-to-use-the-heroku-platform-api)


### Setting up the wrapper

* clone this repo 

* [Install heroku cli](https://devcenter.heroku.com/articles/heroku-cli#download-and-install/) 

* Login to heroku  

    `heroku login`

* You need to generate a token to access the api, do so with the following commands:

    `heroku auth:token` // Gen development token

    `heroku authorizations:create` // Gen OAuth token

* Then use the generated heroku token to create a heroku client

    ```
    let client = Heroku::new("API_KEY_HERE").unwrap();
    let me = client.get().apps().execute::<Value>();
    match me {
        Ok((headers, status, json)) => {
            println!("{:#?}", headers);
            println!("{}", status);
            if let Some(json) = json {
                println!("{}", json);
            }
        }
        Err(e) => println!("Err {}", e),
    }
    ```




