# Website Backend Progress & Token System Update

Hey everyone, here’s a quick update on recent backend progress and the current state of the token system for Astware.

## Website Backend Progress

Over the past few weeks, I’ve transitioned from using GitHub `.js` files to a dedicated Node.js backend to manage blog posts and tokens. This has improved speed and reliability:

- Blog post creation/edit/deletion now takes less than 3 seconds  
- Admin panel is much smoother and updates are nearly instant  
- I now have full control over tokens (verify/unverify), which helps a lot with internal testing and management

This upgrade means users will experience less lag and more consistent updates on the frontend.

## Token Purchase System — Issues & Progress

Right now, the token system works but has a few key challenges I’m still working through.

### Current Issues

- Obfuscation: The current LuaU script is obfuscated but can be easily deobfuscated with AI, making it weak against reverse-engineering  
- Security: Exploiters using HTTP loggers can intercept API requests and potentially access token data or spoof identity

### In Progress

I'm working on better obfuscation and experimenting with different ways to secure HTTP requests, such as:

- Encrypting parts of the logic locally in LuaU  
- Splitting the validation into frontend and backend segments  
- Moving sensitive logic server-side only to reduce exposure

If you're using the token system, don’t share your token and avoid running suspicious scripts while authenticated.

## Previews

Here are some of the features added or improved in the admin panel:

![preview
](https://github.com/AstwareDev/Astware-Website/blob/main/Thumbnails/%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5_2025-05-22_200648818.png?raw=true)
- Tokens list with verify/unverify toggle  
- Blog posts manager with fast update speeds  
- Internal token logs with UserID/IP tracking

## TL;DR

- Backend is now Node.js-based and faster  
- Token validation system is active, but obfuscation still needs work  
- HTTP loggers remain a threat; stay cautious  
- Admin panel is fully functional and no longer relies on GitHub hacks

## Questions or Feedback?

Got ideas or security suggestions? DM me. I'm always open to feedback from devs or exploiters who understand what this is about.

Stay safe,  
Astware Dev
