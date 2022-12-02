# Text-Editor

## Technologies Used

- JavaScript
- Node.js
- express.js
- nodemon.js
- Webpack/plugins
- idb
- babel
- VS Code
- Git
- GitHub

## Summary

This project was an introduction to creating a compress file application using webpack and its plugins to decrease the time to load an application. Webpack allowed us to compress the entire application into a few simple files while babel converted the code to ES5 standards to ensure that the application can run on any browser. We also were able to use manifests to allow the user to download the application and caching the information to a offline database to allow the use of the application offline.

## Demonstration

Deployed Site: https://tranquil-thicket-61391.herokuapp.com/

## Description

A simple text editor site that allows you to download the application from the browser. You can also use the application while offline and your notes will be stored in the offline database. While on the site you can type your notes into the text editor and your typed text will persist even if you refresh or go offline.

## Code Snippet

### Manifest settings to allow the user to download the application

```JavaScript
new WebpackPwaManifest({
        fingerprints: false,
        inject: true,
        name: "Text Editor",
        short_name: "Text",
        description: "Write what you want here!",
        background_color: "#225ca3",
        theme_color: "#225ca3",
        start_url: "/",
        publicPath: "/",
        icons: [
          {
            src: path.resolve("src/images/logo.png"),
            sizes: [96, 128, 192, 256, 384, 512],
            destination: path.join("assets", "icons"),
          },
        ],
      }),
```

### example of a post to the database

```JavaScript
export const putDb = async (content) => {
  console.log("Post to the database");
  const contactDb = await openDB("jate", 1);
  const tx = contactDb.transaction("jate", "readwrite");
  const store = tx.objectStore("jate");
  const request = store.put({ id: 1, content: content });
  const result = await request;
  console.log("data saved to the database", result);
};
```

### example of a get from the database

```JavaScript
export const getDb = async () => {
  console.log("get from the database");
  const contactDb = await openDB("jate", 1);
  const tx = contactDb.transaction("jate", "readonly");
  const store = tx.objectStore("jate");
  const request = store.get(1);
  const result = await request;
  return result?.content;
};
```

## Author Links

[LinkedIn](https://www.linkedin.com/in/kevin-xu-4672a7215/)
[GitHub](https://github.com/KevinPXu)
1
