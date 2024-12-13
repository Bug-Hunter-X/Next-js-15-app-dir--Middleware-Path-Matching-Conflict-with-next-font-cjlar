# Next.js 15 app dir: Middleware Path Matching Conflict with next/font

This repository demonstrates a subtle bug in Next.js 15's `app` directory when using custom middleware with `next/font`.  A poorly constructed regular expression in the middleware can conflict with Next.js's internal font handling, resulting in font loading failures.

## Bug Description

A custom middleware function uses a regular expression to match specific request paths.  If this regex is too broad and overlaps with the internal paths used by `next/font`, it can prevent the fonts from loading correctly. This leads to visual glitches or missing fonts in the application.

## Reproduction

1. Clone this repository.
2. Run `npm install`.
3. Run `npm run dev`.
4. Observe the missing or incorrectly rendered fonts.

## Solution

The solution involves carefully reviewing and refining the regular expression used in the middleware function to avoid conflicts with the `next/font` module.  More specifically, ensure your regex does not unnecessarily match the font related paths.  This often involves more precise matching and potentially using named capture groups to isolate specific parts of the URL.
