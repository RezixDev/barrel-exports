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

