<div align="center">
  <img src="https://avatars.githubusercontent.com/u/202675624?s=400&u=dc72a2b53e8158956a3b672f8e52e39394b6b610&v=4" alt="Flutter News App Toolkit Logo" width="220">
  <h1>Auth API</h1>
  <p><strong>A concrete API implementation of the `AuthClient` interface for the Flutter News App Toolkit.</strong></p>
</div>

<p align="center">
  <img src="https://img.shields.io/badge/coverage-_%25-red?style=for-the-badge" alt="coverage">
  <a href="https://flutter-news-app-full-source-code.github.io/docs/"><img src="https://img.shields.io/badge/LIVE_DOCS-VIEW-slategray?style=for-the-badge" alt="Live Docs: View"></a>
  <a href="https://github.com/flutter-news-app-full-source-code"><img src="https://img.shields.io/badge/MAIN_PROJECT-BROWSE-purple?style=for-the-badge" alt="Main Project: Browse"></a>
</p>

This `auth_api` package provides a concrete API implementation of the `AuthClient` interface (defined in `package:auth_client`) within the [**Flutter News App Full Source Code Toolkit**](https://github.com/flutter-news-app-full-source-code). It encapsulates the logic for interacting with a backend authentication service via HTTP requests, leveraging `package:http_client` for underlying communication and standardized error handling. This package is crucial for applications that need to connect to a remote authentication service, ensuring consistent and robust authentication mechanisms across the Flutter mobile app, web dashboard, and Dart Frog backend API.

## ⭐ Feature Showcase: Robust Backend Authentication Integration

This package offers a comprehensive set of features for integrating with a backend authentication service.

<details>
<summary><strong>🧱 Core Functionality</strong></summary>

### 🚀 `AuthClient` Implementation
- **`AuthApi` Class:** A concrete implementation of the `AuthClient` interface, providing a standardized way to interact with a remote authentication service.
- **HTTP-Based Communication:** Utilizes `package:http_client` for making HTTP requests to the backend authentication service.

### 🔐 Authentication Flows
- **`requestSignInCode`:** Initiates the process of requesting a sign-in code via email.
- **`verifySignInCode`:** Verifies the sign-in code to complete the authentication process.
- **`signInAnonymously`:** Allows users to sign in anonymously, creating a temporary user identity on the backend.
- **`getCurrentUser`:** Retrieves the currently authenticated user's details from the backend.
- **`authStateChanges` Stream:** Provides a stream for monitoring real-time authentication state changes.
- **`signOut`:** Handles signing out the current user from the backend.

### 🛡️ Standardized Error Handling
- **`HttpException` Propagation:** Propagates standardized `HttpException` errors (from `core`) from the underlying `http_client`, ensuring consistent and predictable error management across the application layers.

### 💉 Dependency Injection Ready
- **`HttpClient` Dependency:** Requires a configured `HttpClient` instance (from `package:http_client`) via its constructor, promoting loose coupling and testability.

> **💡 Your Advantage:** This package provides a robust and production-ready API client for backend authentication. It simplifies the integration of remote authentication services, leverages standardized error handling, and ensures consistent authentication flows across your application ecosystem.

</details>

## 🔑 Licensing

This `auth_api` package is an integral part of the [**Flutter News App Full Source Code Toolkit**](https://github.com/flutter-news-app-full-source-code). For comprehensive details regarding licensing, including trial and commercial options for the entire toolkit, please refer to the main toolkit organization page.
