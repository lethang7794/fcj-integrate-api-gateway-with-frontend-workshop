---
title: "Xây dựng ứng dụng frontend của bạn"
weight: 1
chapter: false
pre: " <b> 5.3 </b> "
---

## Xây dựng ứng dụng frontend

1. Đầu tiên, chúng ta cần xây dựng (build) ứng dụng frontend cho môi trường production bằng cách chạy:

   ```shell
   pnpm run build
   ```

2. Lệnh này sẽ chạy `vite build` để tạo ra một gói ứng dụng (application bundle) phù hợp để phục vụ thông qua dịch vụ lưu trữ tĩnh.

3. Kiểm tra gói ứng dụng tại thư mục `dist`

   ```shell
   $ tree dist
   dist
   ├── assets
   │	​​├── 401-BBhoy51U.js
   │	​​├── 403-pH7gA2BX.js
   │	​​├── 404-CUltoGn3.js
   │	​​├── 500-BEjnOsrW.js
   │	​​├── 503-Dw-MojSM.js
   │	​​└── ...
   ├── images
   │	​​├── favicon_light.png
   │	​​├── favicon_light.svg
   │	​​├── favicon.png
   │	​​├── favicon.svg
   │	​​└── shadcn-admin.png
   └── index.html

   3 directories, 69 files
   ```

## Phục vụ ứng dụng frontend trên mạng nội bộ

Bạn có thể sử dụng một máy chủ file để tự phục vụ gói ứng dụng (thư mục `dist`).

Ví dụ: bạn có thể sử dụng [`vercel/serve`](https://github.com/vercel/serve) bằng cách chạy `pnpx serve dist`.

Bây giờ, bất kỳ ai trong mạng nội bộ của bạn (cùng Wifi, LAN) đều có thể truy cập ứng dụng của bạn.

{{<figure src="/images/workshop-3/frontend-app--serve-in-local-network.png" title="" width=300pc >}}
