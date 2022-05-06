# PhotoEditor SDK with Getty Images plugin example

## Requirements to run the example

* Run `yarn`

## Start

1. Run `node app.js`

Open [http://localhost:9191](http://localhost:9191) or [http://localhost:9191/getty](http://localhost:9191/getty) to view it in the browser.

## Initializing the Getty Integration

In order to initialize the `GettyIntegration` invoke the `init` method taking the following arguments:
- `gettyAPIKey` this is your client side Getty API key which you can request [here](https://www.gettyimages.de/solutions/api) by signing up for Getty's developer program
- `gettyTokenURL` refers to the URL that implements the OAuth flow with Getty's resource server. This defaults to the current host with the path `api/token`, see `app.js` for an example implementation.

```
GettyIntegration.init({
  gettyAPIKey: "<YOUR_GETTY_API_KEY>",
  gettyTokenURL: "<AUTH_SERVER_URL>",
});
```

## Configuring the Integration

This integration is a wrapper around IMG.LY's PhotoEditor SDK, so you can configure it in the same way. Refer to the documentation for a full list of [configuration options](https://img.ly/docs/pesdk/web/introduction/configuration/).
In this example, we want to change the label of the export button to 'License Image', so we simply pass a [localization dictionary](https://img.ly/docs/pesdk/web/customization/localization/) to the `init` method:

```
GettyIntegration.init({
  ...,
  custom: {
    languages: {
      en: {
        mainCanvasActions: {
          buttonExport: 'License Image',
        },
      },
    },
  },
});
```

## Configuring the Transform Tool

This Getty integration comes with the PhotoEditor SDK's transform tool enabled by default. Refer to the [official documentation](https://img.ly/docs/pesdk/web/features/transform/) on how to configure this tool.
