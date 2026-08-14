# Source Manifest — Songkran Online

ไฟล์ ZIP ที่ส่งมอบใช้โครงสร้างนี้เป็นลำดับอ้างอิงของซอร์สโค้ดทั้งหมด โดย **ไม่รวม** `node_modules/`, `dist/`, `.git/`, `.manus-logs/`, ไฟล์ `.env*`, coverage และ log เพื่อไม่ให้มี dependencies ที่ติดตั้งซ้ำได้, build output หรือข้อมูลลับติดไปด้วย

## 1. จุดเริ่มต้นและการตั้งค่าโครงการ

```text
package.json
pnpm-lock.yaml
vite.config.ts
vitest.config.ts
tsconfig.json
tsconfig.node.json
drizzle.config.ts
components.json
template.json
.gitignore
.prettierignore
.prettierrc
patches/wouter@3.7.1.patch
```

## 2. หน้าเว็บ React และสไตล์

```text
client/index.html
client/src/main.tsx
client/src/App.tsx
client/src/const.ts
client/src/index.css
client/src/poster-overrides.css
client/src/wish-form.css
client/src/pages/Home.tsx
client/src/pages/NotFound.tsx
client/src/pages/ComponentShowcase.tsx
client/src/lib/trpc.ts
client/src/lib/utils.ts
client/src/contexts/ThemeContext.tsx
client/src/hooks/useComposition.ts
client/src/hooks/useMobile.tsx
client/src/hooks/usePersistFn.ts
client/src/_core/hooks/useAuth.ts
client/src/components/ErrorBoundary.tsx
client/src/components/ManusDialog.tsx
client/src/components/Map.tsx
client/src/components/AIChatBox.tsx
client/src/components/DashboardLayout.tsx
client/src/components/DashboardLayoutSkeleton.tsx
client/src/components/ui/*.tsx
```

> `client/src/pages/Home.tsx` คือไฟล์เนื้อหาและ UI หลักของเว็บไซต์ ส่วน `index.css`, `poster-overrides.css` และ `wish-form.css` กำหนดสไตล์โปสเตอร์, responsive layout และแบบฟอร์มคำอวยพร

## 3. ระบบเซิร์ฟเวอร์, tRPC และการทดสอบ

```text
server/routers.ts
server/db.ts
server/storage.ts
server/index.ts
server/auth.logout.test.ts
server/songkranWishes.test.ts
server/_core/context.ts
server/_core/cookies.ts
server/_core/dataApi.ts
server/_core/env.ts
server/_core/heartbeat.ts
server/_core/imageGeneration.ts
server/_core/index.ts
server/_core/llm.ts
server/_core/map.ts
server/_core/notification.ts
server/_core/oauth.ts
server/_core/sdk.ts
server/_core/storageProxy.ts
server/_core/systemRouter.ts
server/_core/trpc.ts
server/_core/vite.ts
server/_core/voiceTranscription.ts
server/_core/types/cookie.d.ts
server/_core/types/manusTypes.ts
```

## 4. Database schema และ migration

```text
drizzle/schema.ts
drizzle/relations.ts
drizzle/0000_absent_supreme_intelligence.sql
drizzle/meta/0000_snapshot.json
drizzle/meta/_journal.json
drizzle/migrations/.gitkeep
```

## 5. Shared contracts, เอกสาร และไฟล์ public ขนาดเล็ก

```text
shared/const.ts
shared/types.ts
shared/_core/errors.ts
client/public/.gitkeep
client/public/__manus__/debug-collector.js
client/public/__manus__/version.json
EDITING_GUIDE.md
browser-verification.md
ideas.md
todo.md
```

## 6. ไฟล์ standalone ที่อยู่นอกโฟลเดอร์โครงการ

```text
songkran-online-standalone-fixed.html
```

ไฟล์ standalone ถูกวางไว้ที่ root ของ ZIP เพื่อให้เปิดใช้งานแยกจากระบบ React ได้ทันที ทั้งนี้ไฟล์ดังกล่าวใช้สำหรับหน้าเว็บแบบ static จึงไม่มี backend สำหรับบันทึกคำอวยพรจริง
