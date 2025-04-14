# Next.js 15 Hydration Error in Kakao WebView

This repository demonstrates a hydration error that occurs specifically in the Kakao Talk WebView environment when using Next.js 15.3.0 in development mode.

## Issue Description

When accessing a Next.js 15.3.0 application through the Kakao Talk WebView in development mode, hydration errors appear in the console:

```
Hydration failed because the server rendered HTML didn't match the client. As a result this tree will be regenerated on the client.
```

This happens even with a completely fresh Next.js project without any custom code or problematic patterns (no `Math.random()`, no date formatting, no conditional rendering).

## Important Notes

- This issue only occurs with Next.js 15.3.0 (not with previous versions like 14.x)
- The issue only appears in development mode (`npm run dev`) and not in production builds
- The error is specific to the Kakao Talk WebView environment on iOS

## Environment Details

- Next.js: 15.3.0
- React: 19.0.0
- Device: iPhone with iOS 17.6.1
- Kakao Talk app version: 25.2.2
- WebView Engine: AppleWebKit/605.1.15 (Safari WebView)

User Agent string:

```
Mozilla/5.0 (iPhone; CPU iPhone OS 17_6_1 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Mobile/15E148 Safari/604.1 KAKAOTALK/25.2.2 (INAPP)
```

## Steps to Reproduce

1. Clone this repository:

   ```bash
   git clone https://github.com/ssolfa/nextjs-15-kakao-webview-hydration-issue.git
   cd nextjs-kakao-webview-issue
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Start the development server with network access:

   ```bash
   npm run dev -- -H 0.0.0.0
   ```

4. Note your computer's IP address

5. Share the link `http://[your-ip-address]:3000` in a Kakao Talk chat

6. Open the link using the Kakao Talk internal WebView

7. Check the console (if using remote debugging) to observe the hydration error

## Screenshots

https://github.com/user-attachments/assets/db3389ad-f718-4f1f-970c-5052a6d838c3

## Additional Information

- The page still functions correctly despite the hydration error
- This issue affects Korean developers significantly as Kakao Talk is one of the primary platforms for sharing web content in Korea
- The problem does not occur in regular browsers or other WebViews

## Comparison with Next.js 14

To verify this is specific to Next.js 15, you can modify the `package.json` to use Next.js 14:

```json
"dependencies": {
  "next": "14.0.4",
  "react": "^18.2.0",
  "react-dom": "^18.2.0"
}
```

After running `npm install` and repeating the steps above, you'll see that the hydration error does not occur in Next.js 14.
