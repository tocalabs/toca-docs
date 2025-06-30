# Testing Apps

Testing your App before you put it in the hands of your users is an essential part of the development lifecycle. It allows you to check that the interface looks as you expect it to whilst also allowing you to validate that your app behaves like it should. Testing your App then gives you confidence that your App is ready for your users!


## Preview Mode

When you are building your App in the App Designer, you are typically using "Design Mode". When you are in design mode, you can drag components onto the page, edit the properties of your components and define your In Page Logic (IPL). Design mode is aimed at making it as easy as possibly to build your app so while it can give you a rough idea of how your page will look there are certain limitations to how components can be rendered. Fortunately to solve this, the App Designer has another mode: preview mode.

Preview mode solves this for you by taking away the distractions of the App Designer and showing you the App as your end users would see it. Your App, as shown in preview mode, will look exactly the same as it would once you have deployed it.

Whilst in preview mode, you can click on links to other pages and they will work as expected, your IPL will also work as expected.

> _**Note 📝**_
>
> _Preview mode allows you to see your App as your users would, but as you are still viewing the App within the Toca platform, it will perform a bit slower than your real deployed app, particularly if there is lots of IPL or data being rendered on the page._

### Previewing as a User

If your app is set up to to use :docs-link[authentication]{id="projects/apps/authentication"}, then you may well have designed your app so that users with different roles are allowed to see different data and perform different actions. This is typically done by setting up permissions on either your pages or the resources linked to your app. To test how your permissions work on your App, you can use the "Preview as User" feature, which allows you to enter preview mode as a particular user that has been set up on your app.

This can be extremely useful for debugging issues that users might encounter as you can experience using the App exactly as they do.

## Using Deploy States

Just like with automation, your Apps are always :docs-link[versioned]{id="common/versioning"}, this means that you can develop your app in the _Draft_ state, whilst your _Published_ state app is the one that is deployed and in the hands of your users. You can have your draft state deployed on one URL and your published version deployed on another URL. This allows you to fully :docs-link[deploy your App]{id="projects/apps/deployment"} whilst developing it so you can see what the real experience will be like.

## Using Deploy Targets

In addition to the deploy states, you can also deploy your App to multiple different URL's. This means that you can make some changes to your App then deploy it to a new URL, this can allow you to perform [A/B Testing](https://en.wikipedia.org/wiki/A/B_testing). Fully deploying your App to test it can also give you a much better idea of how your app will be perform for users, as even though the preview mode in the App Designer is very practical for testing, nothing quite substitutes for real thing!
