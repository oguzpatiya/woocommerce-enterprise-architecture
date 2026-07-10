# WooCommerce Enterprise Architecture Guidelines

This repository serves as a foundational blueprint for developing, scaling, and maintaining high-performance e-commerce environments. It addresses the critical architectural conflicts between complex page builders and aggressive edge-caching networks.

## Core Objective
To democratize enterprise-grade web performance by providing strict configuration standards that prevent site-breaking updates, CSS rendering failures, and asynchronous loading conflicts in dynamic e-commerce platforms.

## Architectural Standards (Draft v1.0)

### 1. The Stability Rule for Page Builders
When utilizing visual DOM generators (e.g., Elementor) alongside advanced caching mechanisms (e.g., LiteSpeed + CDN), specific optimization features must be explicitly disabled to prevent structural degradation:

*   **CSS Combine:** Strictly `OFF`. Forcing combination disrupts the isolated CSS delivery method required by dynamic widgets.
*   **Generate UCSS (Unused CSS):** Strictly `OFF`. Automated removal frequently strips critical hidden states (like mobile menus and modal triggers).
*   **Load CSS Asynchronously:** Strictly `OFF`. This prevents Flash of Unstyled Content (FOUC) and critical layout shifts on product pages.

*Note: Minification should remain active as a baseline optimization.*

### 2. Edge WAF & Bot Mitigation
Security protocols at the CDN level (e.g., Quic.cloud) must be calibrated for e-commerce traffic. Aggressive rules like URL Flood Protection or strict Bot Detection must be balanced to prevent false-positive CAPTCHA blocks for legitimate buyers, ensuring seamless UX.

---
*Maintained by the Open Source E-commerce Architecture Initiative.*
