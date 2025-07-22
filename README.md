# auth_api

![coverage: 98%](https://img.shields.io/badge/coverage-98-green)
[![style: very good analysis](https://img.shields.io/badge/style-very_good_analysis-B22C89.svg)](https://pub.dev/packages/very_good_analysis)
[![License: PolyForm Free Trial](https://img.shields.io/badge/License-PolyForm%20Free%20Trial-blue)](https://polyformproject.org/licenses/free-trial/1.0.0)

Concrete API implementation of the `AuthClient` interface defined in
`package:auth_client`. This package provides the logic for interacting
with a backend authentication service via HTTP requests using
`package:http_client`.

## Getting Started

Add this package to your `pubspec.yaml` dependencies:

```yaml
dependencies:
  auth_api:
    git:
      url: https://github.com/flutter-news-app-full-source-code/auth-api.git
      # Optionally specify a ref (branch, tag, commit hash)
      # ref: main
```

You also need to include `http_client` and `auth_client` (which this
package depends on).

## Features

Provides an `AuthApi` class implementing `AuthClient` with the following
capabilities:

*   Requesting a sign-in code via email (`requestSignInCode`).
*   Verifying the sign-in code to complete authentication (`verifySignInCode`).
*   Signing in anonymously (`signInAnonymously`).
*   Retrieving the current authenticated user (`getCurrentUser`).
*   Monitoring authentication state changes via a stream (`authStateChanges`).
*   Signing out the current user (`signOut`).

## Usage

Instantiate `AuthApi` with a configured `HttpClient` instance:

```dart
import 'package:auth_api/auth_api.dart';
import 'package:auth_client/auth_client.dart';
import 'package:http_client/http_client.dart';

void main() async {
  // Configure HttpClient (replace with your actual base URL and token logic)
  final httpClient = HttpClient(
    baseUrl: 'https://your-api.com',
    tokenProvider: () async => 'YOUR_AUTH_TOKEN', // Or null if not logged in
  );

  // Create the auth API client
  final AuthClient authClient = AuthApi(httpClient: httpClient);

  // Listen to authentication state changes
  authClient.authStateChanges.listen((user) {
    if (user != null) {
      // To check for an anonymous user, you would typically check their role,
      // e.g., if (user.role == UserRole.guestUser) { ... }
      // Assuming UserRole enum is accessible/imported.
      print('User signed in: ${user.id}, Role: ${user.role}');
    } else {
      print('User signed out.');
    }
  });

  try {
    // Example: Request sign-in code
    await authClient.requestSignInCode('user@example.com');
    print('Sign-in code requested.');

    // Example: Verify code (replace '123456' with actual code)
    // final authResponse = await authClient.verifySignInCode('user@example.com', '123456');
    // print('User verified: ${authResponse.user.id}, Token: ${authResponse.token}');

    // Example: Sign in anonymously
    // final anonAuthResponse = await authClient.signInAnonymously();
    // print('Signed in anonymously: ${anonAuthResponse.user.id}, Token: ${anonAuthResponse.token}');

    // Example: Get current user
    // final currentUser = await authClient.getCurrentUser();
    // if (currentUser != null) { ... }

    // Example: Sign out
    // await authClient.signOut();

  } on HttpException catch (e) {
    print('Authentication error: $e');
  } finally {
    // Remember to dispose the client if it has resources like streams
    // (In this specific implementation, AuthApi has a dispose method)
    (authClient as AuthApi).dispose();
  }
}

```



## 🔑 Licensing

This package is source-available and licensed under the [PolyForm Free Trial 1.0.0](LICENSE). Please review the terms before use.

For commercial licensing options that grant the right to build and distribute unlimited applications, please visit the main [**Flutter News App - Full Source Code Toolkit**](https://github.com/flutter-news-app-full-source-code) organization.
