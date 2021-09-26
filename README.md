# Every-Layout-Reel-Test
Test environment to identify conflict between Reel, Center and Reel Components in every-layout.dev

There is an issue with the Reel Component that results in horizontal scrolling on the webpage and not just within the Reel Component itself. I have attempted to troubleshoot and I have narrowed the issue which I will now describe below.

The horizontal scrolling issue arises under the following conditions:
1. You are on a small viewport (set your browser Inspector to Samsung/iPhone screen)
2. There is a Reel Component
2. The Reel has a Center Component as its parent
3. The Center Component has a Stack Component as its parent

The cause of the issue presents itself as such:

The use of <code>margin-left: auto;</code> and <code>margin-right: auto;</code> in the Center Component conflicts with something in the child Reel Component or in its parent Stack Component, I cannot confirm what it is yet. This also means that you cannot use a Container Class to limit content to a max-width as it relies <code>margin-left: auto;</code> and <code>margin-right: auto;</code> as well.

Suffice to say that once you delete <code>margin-left: auto;</code> and <code>margin-right: auto;</code> on the Center Component/Container Class, the horizontal scrolling no longer happens.

If you decide that centering the Reel Component is important and therefore refuse to delete the <code>margin-left: auto;</code> and <code>margin-right: auto</code> from the Center Component, there is one other way to fix the horizontal scrolling issue on small screen sizes:

If you remove <code>display:flex;</code> from the Stack Component, the horizontal scrolling on small screen sizes disappears. Hence the use of <code>display:flex;</code> in the Stack Component conflicts with something in the Reel Component or Center Component. The trade-off is that I cannot space elements using the Stack anymore.

So far, the narrowwed cause of conflict is definitely a margin issue, but I sadly cannot pin-point beyond this. Perhaps you could help figure it out?
