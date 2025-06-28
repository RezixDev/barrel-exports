# To Barrel or not to Barrel, that is the Question

Every once and then we get the same answer, or warning that you should not in fact use Barrel Exports.
Why? Bacause of Tree-Shaking which causes large bundle sizes and performance issues while bundling.

I fund in the Internet this Article:

https://laniewski.me/blog/pitfalls-of-barrel-files-in-javascript-modules/

and this Reddit post:

https://www.reddit.com/r/reactjs/comments/1ggpyms/vite_and_barrel_files_performance_issues/


So... what is my Experince? Do Barrel Exports make that a huge difference?

Let's test it out!

I made an Nutrition Component for saving meals in my Health Tracker.

First with Simple Structure: 4 files. Than rebuild it into more Enterprise Structure. The problem is, that the Refactoring with Claude gave me a lot of Barrel Exports. 

I guess this is a great opportunity to make an Experiment.

How big is the Bundle Size and performance of bundling the Project using Barrel Files?

Client-side bundling built in 3.40s

Server-side (SSR + Nitro) bundling built in:

- ~1.3s (vite SSR)
- ~3s (Nitro server)

Total size: 5.8 MB (1.33 MB gzip)

So i decided to refactor my Project. What is the outcome?

https://github.com/RezixDev/Gym-Tracker/commit/b8225519ba06e76091c7aba39c034db123e0c119

And what are the Times be after?

| Build Phase   | With Barrel Imports | Without Barrel Imports | Difference  |
| ------------- | ------------------- | ---------------------- | ----------- |
| Client (Vite) | 3.40s               | 3.19s                  | **-0.21s**  |
| SSR (Vite)    | 1.29s               | 1.21s                  | **-0.08s**  |
| Nitro (Node)  | \~3s                | \~3s                   | ≈ 0s        |
| **Total**     | \~7.7s              | \~7.4s                 | **≈ -0.3s** |

Number of transformed modules:

Before: 2412

After: 2395 → 17 fewer modules (possibly due to tree-shaking + no barrel re-exports)

So i guess it's worth it. 
We have way fewer files, the build time is a little bit faster and the Project is cleaner. And it was only one feature! Imagine what could the outcomes be if we had an bigger Project!


