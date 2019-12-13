![](https://media.giphy.com/media/Idz7cyLRe2bVm/giphy.gif)

---

# What is Storybook?

![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)

---

# Document your front-end components!

https://storybook.js.org/docs/guides/guide-react/

![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)


---

# How to I get access to this wizardry?

In Vanilla repo run:

`yarn storybook`


![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)

---

# How to I add a new "story" ?

Say you had a component called `MyCoolComponent.tsx`, make a file next to it called `myCoolComponent.story.ts` It will automatically get picked up by storybook.


![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)

---

# How do I add a story?

![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)

---

# 1. Create a "group"

`const story = storiesOf("Forms", module);`

The string you put there is the first level that shows up in the panel. Example, this is part of a group of elements we find in "Forms";

![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)

---

# 2. Create a "story"

Then add the page about your component(s):

```
story.add("Results", () => {
    return <MyCoolFormInput/>;
});
```

You can add as many "stories" as you want in this file.


![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)

---

# Chromatic

https://www.chromaticqa.com/

Tool we use to catch visual changes

![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)

---

# Chromatic takes screen shots when you make a PR. They need to be approved.

![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)

---

## Example of new pages:
https://www.chromaticqa.com/build?appId=5d5eba16c782b600204ba187&number=1395

## Example of change:
https://www.chromaticqa.com/snapshot?appId=5d5eba16c782b600204ba187&id=5de169eaeaa7e00020f9a938


![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)

---


# Questions?

![](https://media.giphy.com/media/EA3RHPEx6BlBu/giphy.gif)
