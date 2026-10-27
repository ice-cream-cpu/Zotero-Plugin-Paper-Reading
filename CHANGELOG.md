# Changelog

## 0.6.15 - 2026-10-27

### 简体中文

- 更新插件管理器和右下角固定入口的专属图片图标；悬停时仅轮廓发光，不显示矩形背景。
- Settings 展开时为绿色，收起时为灰色。
- 修复 Provider 切换；Model 菜单按当前提供方与 Endpoint 展示对应厂家的模型。
- 自动记忆各提供方的 Endpoint、密钥和模型配置。
- 为长对话加入每轮提问的快速导航。
- 改善历史会话中的 Markdown、表格和数学公式显示；公式仅在实际溢出时显示横向滑动控件。
- 更新中英文安装、配置和使用说明。

### English

- Added custom plugin-manager artwork and a fixed bottom-right image launcher with a contour-only hover glow.
- Settings is green while expanded and gray while collapsed.
- Fixed Provider switching and filtered Model choices by the selected provider and endpoint.
- Remembered provider-specific endpoints, keys, and models locally.
- Added question-by-question navigation for long conversations.
- Improved restored Markdown, table, and equation rendering, with equation controls only on actual overflow.
- Updated the Chinese and English installation, configuration, and usage guides.

This release includes the user-facing improvements since 0.6.4. Existing conversation history and API preferences are preserved when updating.

## 0.6.4 - 2026-10-25

- Expanded the Zotero compatibility ceiling to `99.0.*`, preventing future major-version bumps from disabling the plugin solely because of its version range.
- Retained Zotero 9.0 as the minimum supported version and verified installation on Zotero 10.0.6.
- Replaced the Zotero-major-specific package name with `ice-cream-0.6.4.xpi`.
- Corrected the development manifest to use the public GitHub homepage and update manifest.

## 0.6.3 - 2026-08-25

- Added permanent per-conversation deletion controls.
- Preserved the active conversation when deleting another history entry.
- Automatically loads the newest remaining conversation after deleting the active entry.
- Creates one empty conversation when no saved conversations remain.

See `README.md` for the complete feature and usage documentation.
