[<img width="40" src="https://cdn.simpleicons.org/googlesummerofcode" />](#) &nbsp;[<img width="230" src="https://cdn.prod.website-files.com/611a19b9853b7414a0f6b3f6/611bbb87319adfd903b90f24_logoRC.svg" />](#)  
Google Summer of Code 2025 for Rocket.Chat

# 🚀 Real Time Message Rendering in Message Composer
Hello, this is Ishan! I created this repository as a dedicated hub for my final work product submission, which illustrates and highlights my contributions to Rocket.Chat during Google Summer of Code - 2025. 

## 💡Work Highlights 
1. [Pull Request](https://github.com/RocketChat/Rocket.Chat/pull/35975)
2. [Project Showcase](https://composer.ishanmitra.com/)

## 🧠 About the Project
_The Message Composer refers to Rocket.Chat's textbox component inside the chatroom. It includes the textbox where users can type messages, use the formatter buttons, and attach files._  

The project implements real-time rendering of the user's text message, including **bold**, _italics_, and ~~strikethrough~~, as well as converting emoji text shortcodes such as `:rocket:` to 🚀.
This quality-of-life feature is much needed, as it allows users to quickly preview the outcome of their message before sending, rather than looking at raw Markdown plaintext, such as `_this_`.

## 🛣️ Project Milestones
- [x] Develop a new `RichTextComposer` component with rich-text support
- [x] Create a Storybook component to ensure the integrity of the design is maintained
- [x] Implement backward-compatible APIs for the `RichTextComposer` component to maintain integrity with the old `Composer`
- [x] Support keyboard interactions for formatting shortcuts and message navigation 
- [x] Verify consistent behavior across Chromium-based and Firefox-based browsers 
- [x] Render bold, italics, strikethrough, and inline code as the user types
- [x] Render username mentions, `@all`, `@here`
- [x] Convert emoji shortcodes to Unicode emojis<sup>1</sup>
- [x] Render custom server emojis to images<sup>1, 2</sup>
- [ ] Ensure user can undo or redo edits<sup>3</sup>
- [ ] Render unordered lists, ordered lists, quote blocks, multiline code, KaTeX, tables
- [ ] Handle rendering on drag-and-drop, copy-paste, cut-paste<sup>4</sup>

<sup>1</sup> Cursor jumps to the start of the message when a shorthand converts to an emoji in the parent `Composer`. This affects the `RichTextComposer`.  
<sup>2</sup> Limited support. Rendition logic needs refinement, as non-text assets (e.g., GIFs) don’t preserve the original shorthand.  
<sup>3</sup> Unsupported. Rich text rendition logic destroys edit history. Requires implementation of the edit history stack. Keyboard shortcuts don't work.  
<sup>4</sup> Limited support. Cut-paste and Copy-paste events work. Drag-and-drop causes glitches.

## 📚 Commit Timeline
The following table lists key commits from the pull request. It highlights only the most important changes made during the development of the `RichTextComposer`.  
|                                   Commit                                        | Short description                                                                                 |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| [4bad5c1](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/4bad5c1) | Replace `textarea` with `contenteditable` inside `ComposerMessageInput`                           |
| [7f97121](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/7f97121) | Implement `getSelectionRange` / `setSelectionRange` as replacements for `textarea` selection APIs |
| [b999a60](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/b999a60) | Implement cursor tracking so formatter button clicks work correctly                               |
| [43d567b](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/43d567b) | Add a placeholder inside the `RichTextComposer` component                                         |
| [3f77840](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/3f77840) | Update `getSelectionRange` / `setSelectionRange` to traverse DOM tree structures                  |
| [21d4e8b](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/21d4e8b) | _@MartinSchoeler:_ Wrapping `RichTextComposer` inside `FeaturePreview`                            |
| [1f4562e](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/1f4562e) | Update `contenteditable` from `div` to `span` for better cross-browser inline support             |
| [949e19f](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/949e19f) | Add composer state handlers to track text/cursor on edit events in render pipeline                |
| [322744b](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/322744b) | Integrate Gazzodown `parseMessage` helper function to parse AST in the render pipeline            |
| [39c2b5d](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/39c2b5d) | Implement `messageParser` to convert AST to HTML in the rich text rendering pipeline              |
| [8103d3f](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/8103d3f) | Implement shortcode to native Unicode character or custom emoji image                             |
| [e730794](https://github.com/RocketChat/Rocket.Chat/pull/35975/commits/e730794) | Final commit during the Coding Period of Google Summer of Code 2025                               |

The deliverables have been largely implemented, though there is still room for improvement. Additional commits will be pushed to the PR after the conclusion of GSoC.
This project was developed in tandem with the AI Enhanced Message Composer Component, which builds upon the new `RichTextComposer` component.

## 📽️ Project Showcase
https://github.com/user-attachments/assets/506a8b98-133c-4959-ba5e-326dca5c8b24

## 🏄‍♂️ Challenges
- Different browsers handle text input inside `contenteditable` in very different ways, often leading to unexpected inconsistencies.
- A script that runs smoothly on Chromium often breaks on Firefox unless carefully accounted for.
- Using `execCommand` within an `input` event caused highly unpredictable behavior, making it clear this approach should be avoided.
- While the core pipeline design was straightforward, the overall scale and complexity of the monorepo significantly increased the implementation effort.

## 🔮 Future Goals
- Bugfixes in both the original `Composer` and `RichTextComposer`
- Add support for more advanced Markdown layouts, such as code blocks with syntax highlighting
- Work on the React Native client to bring this feature to Android and iOS smartphones

## ☀️ Mentors
I am very grateful to my mentors, who encouraged me to work with a strong sense of teamwork and discipline. Since I was working closely with another GSoC contributor, this guidance became even more valuable.
Their technical advice and focus on making small, meaningful commits helped me improve both my collaboration skills and my work approach.
1. Martin Schoeler - Mentor &nbsp;
[<img height="18" width="18" src="https://cdn.simpleicons.org/rocketdotchat/f5455c/white" />](https://open.rocket.chat/direct/martin.schoeler)
[<img height="18" width="18" src="https://cdn.simpleicons.org/github/black/white" />](https://github.com/MartinSchoeler) 
2. Sing Li - Mentor &nbsp;
[<img height="18" width="18" src="https://cdn.simpleicons.org/rocketdotchat/f5455c/white" />](https://open.rocket.chat/direct/sing.li)
[<img height="18" width="18" src="https://cdn.simpleicons.org/github/black/white" />](https://github.com/Sing-Li)

## 🤝 Further Thanks
I wish to thank two other mentors and my fellow GSoC contributor. Their extended support is extremely appreciated.
1. Ayush Jitendra Kumar - GSoC Contributor &nbsp;
[<img height="18" width="18" src="https://cdn.simpleicons.org/rocketdotchat/f5455c/white" />](https://open.rocket.chat/direct/ayush.jitendra)
[<img height="18" width="18" src="https://cdn.simpleicons.org/github/black/white" />](https://github.com/AyushKumar123456789) 
2. Zishan Ahmed - Mentor &nbsp;
[<img height="18" width="18" src="https://cdn.simpleicons.org/rocketdotchat/f5455c/white" />](https://open.rocket.chat/direct/zishan.ahmad)
[<img height="18" width="18" src="https://cdn.simpleicons.org/github/black/white" />](https://github.com/Spiral-Memory)
3. Gabriel Engel - Mentor &nbsp;
[<img height="18" width="18" src="https://upload.wikimedia.org/wikipedia/commons/8/81/LinkedIn_icon.svg" />](https://www.linkedin.com/in/gabrielengel/)