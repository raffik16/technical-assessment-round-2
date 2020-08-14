# Technical Assessment - Round 2

A more advanced Vue component to build, and sample components to code review. Used at Funkhaus as a Technical Assessment test for prospective engineers.

## Task

1.  Build a complicated Vue component to the required design.
1.  Written code reviews of 3 components.

## Design

The XD file can be seen in browser here:
https://xd.adobe.com/view/91370cf5-0ce3-46c4-94e1-f0033df25fa3-c464/

The XD design prototype is limited, please see this movie for a better explanation of the required motion and timing:
https://www.dropbox.com/sh/1oc5bccnky06l7a/AABiiOkGr7WGSyljFU2RLTtZa?dl=0&preview=Funkhaus+Slideshow+Component+Sample+-+Animation.mp4

**Notes**

1.  XD does allow you to see the specs of all the elements. Click the `</>` button in top right corner.
1.  You can download assets (images, SVGs, etc) from XD.
1.  Please use your best judgement to make this design responsive.
1.  Take note the hover state when hovering over the title in the center of the screen.
1.  Fonts can be found [here](https://www.dropbox.com/sh/1oc5bccnky06l7a/AAB3IYxh15-gyq60TR8GvrsZa/Fonts?dl=0).
1.  The text in the corners need a cool hover state (please build as you like), but they don't need to link anywhere.

### Requirements

Imagine this design is the home page to an entire website. So setup basic structure and any sub-components as you would if you were going to be building out a site from this starting point.

1.  Please use the [Nuxt framework](https://nuxtjs.org/guide/installation#starting-from-scratch).
1.  Please keep SEO in mind when you build this. We want to see that you understand HTML semantics.d.
1.  No CSS frameworks please.
1.  Please no Vue plugins, we want to see you know how to build complicated UI from scratch.

**Hints**

1.  Please [read this a guide](https://github.com/funkhaus/best-practices/blob/master/README.md) for our best practices.
1.  Please [see this sample component](https://github.com/funkhaus/factory/blob/master/src/components/WorkBlock/BlockWork.vue) for an expectation on quality style.

### Mock data

The included `/db.json` file should be used as your mock API, but accessed via this URL:

`https://raw.githubusercontent.com/funkhaus/technical-assessment-round-2/master/db.json`

1.  The list of slides can be generated from the `pages` array.
1.  Note the `siteMeta` and `page` objects, those can be used for SEO.
1.  The `menu` array can be used to build the the top-right corner menu.
1.  Use the Nuxt fetch method to read the JSON file from GitHub.

### Deploy & Submit

Please deploy to Netlify or Vercel. The free tier is fine.

Please share a repo of your code to the GitHub user `drewbaker` (or email to drew@funkhaus.us).

## Component Code Reviews

The `/components` directory includes 3 sample Vue components. Please review them and provide feedback as you would to the programming team at Funkhaus. You can do these using GitHub issues (or PR's if you're comfortable with that) on the repo you submit. If you have a better way you like to handoff code reviews, please feel free to do them that way.

You don't need to review the components in `/components/includes`. Those are only included as they are used by the other components, so you can use them for your review.

These are Nuxt components, so it will easy for you to just add them into a Nuxt project. See the `/pages/review.vue` which you can drop into a sample Nuxt project.

### Design

The components are shown in a design here: https://xd.adobe.com/view/543493df-b724-4eec-7a88-6c281092d77e-2205/

**Hints**

1.  Please [read this a guide](https://github.com/funkhaus/best-practices/blob/master/README.md) for our best practices.
1.  Please [see this sample component](https://github.com/funkhaus/factory/blob/master/src/components/WorkBlock/BlockWork.vue) for an expectation on quality style.
1.  This is [another good sample component](https://github.com/funkhaus/components/edit/master/src/components/InstagramFeed.vue), although the `await on line 32` should use `try/catch` block not a `then()` promise chain.
1.  Please [see this for an overview of our CSS philosophy](https://maintainablecss.com/chapters/semantics/).
