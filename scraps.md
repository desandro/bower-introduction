In order to make websites, we have to make the build blocks of web sites.

---

Building stuff on top of stuff. Going more than 2 layers deep

---

I could go on and explain more of what Bower is. That you can point to your own git endpoints, your set up your own internal shorthand, and how to register your packages. But that's what the docs are for. Go ahead, and go to bower.io and read up. It's all there. That is the _what_ of Bower. From here on out, I want to talk about the _why_ of Bower.



---

Yes, I work at Twitter. And yes, I have contributed to Bower. But the reason I stand here today is not just to proslytize an assignment. I am excited to talk about Bower, becuase it's honestly worked for me as a user. I needed it for my own projects. I needed it, and since adopting it 8 months ago, I've found success. I'd like to share that with you.

---

Encapsulation is important because it breaks down large, unruly things, into smaller pieces. Smaller pieces are easier to understand. We can only fit so much into our heads at one point. When you are working on a component, you can simplify the story.

---

We shouldn't be commiting projects inside of one other.

---

Bringing over the same principles of coding, into how we manage projects.

- Encapsulation
- DRY
- 

---

In the current front-end resource ecosystem, each solution works independently of one another. Yes there is interoperability, so two resources can work together. But there is little dependency, where a resource works by relying on another. For the most part, resources are siloed.

If there is any dependency, it is likely to be on a framework, like jQuery or Bootstrap or Foundation, or on utility library, like Underscore/lo-dash. If our front-end applications had a struture, it would be especially flat, with few levels.

What this means is that each resource must be built in such a way that it can stand up on its own. Each resource must maintain considerable structure.

I don't mean to say that the resources we have now are bloated and oversized. However, the logic within current resources is cumbersome.

