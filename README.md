# Minimal nue bug reproduction

I can't seem to get hot reloading to work when I'm editing `.dhtml` files.

Here's what I did
- Created a new blog template
```sh
nue create simple-blog
```

- Edited the `contact/contact.dhtml` file
```diff
  <label>
    <span>Your name</span>
    <input type="text" name="name" placeholder="Example: John Doe" required>
  </label>

+  <label>
+    <span>Your favorite game</span>
+    <input type="text" name="game" placeholder="Example: Tekken 8" required>
+  </label>

  <label>
    <span>Your email</span>
    <input type="email" name="email" placeholder="your@email.com" required>
  </label>
```

At this point, I expected the changes to be visible on the `/contact/` page.

- Refreshed the page (currently in Brave with shields down)

No change.

- Stopped and restarted the server

```sh
^C
nue
````

Still no change.

- Stop the server.
- Remove the `.dist` directory
- Restart the server
```sh
^C
rm -rf .dist
nue
```

At this point I finally see my changes in the `contact.dhtml` component.

## Expected behavior

I expect that when I make a change to a component, nue rebuilds it and my web page is updated.

## Environment

OS: Ubuntu 24.04.1 LTS
Nuekit version & JS runtime: Nue 1.0.0-RC.2 Bun 1.1.45 

