# google_sign_in

[![pub package](https://img.shields.io/pub/v/google_sign_in.svg)](https://pub.dartlang.org/packages/google_sign_in)

A Flutter plugin for [Google Sign In](https://developers.google.com/identity/).

*Note*: This plugin is still under development, and some APIs might not be available yet. [Feedback](https://github.com/flutter/flutter/issues) and [Pull Requests](https://github.com/flutter/plugins/pulls) are most welcome!

## Android integration

To access Google Sign-In, you'll need to make sure to [register your
application](https://developers.google.com/mobile/add?platform=android).

You don't need to include the google-services.json file in your app unless you
are using Google services that require it. You do need to enable the OAuth APIs
that you want, using the [Google Cloud Platform API
manager](https://console.developers.google.com/). For example, if you
want to mimic the behavior of the Google Sign-In sample app, you'll need to
enable the [Google People API](https://developers.google.com/people/).

## iOS integration

1. [First register your application](https://developers.google.com/mobile/add?platform=ios).
2. Open Xcode. You'll have to paste this into Xcode to properly register `GoogleServices-Info.plist`.
3. Select `GoogleServices-Info.plist` from the file manager and drag that file into the `Runner` directory, `[my_project]/ios/Runner/GoogleServices-Info.plist`.
4. A dialog will show up and ask you to select the targets, select the `Runner` target.  
5. Then add the `CFBundleURLTypes` attributes below into the `[my_project]/ios/Runner/Info.plist` file.  

```
<!-- Put me in the [my_project]/ios/Runner/Info.plist file -->
<!-- Google Sign-in Section -->
<key>CFBundleURLTypes</key>
<array>
	<dict>
		<key>CFBundleTypeRole</key>
		<string>Editor</string>
		<key>CFBundleURLSchemes</key>
		<array>
			<!-- TODO Replace this value: -->
			<!-- Copied from GoogleServices-Info.plist key REVERSE_CLIENT_ID -->
			<string>com.googleusercontent.apps.861823949799-vc35cprkp249096uujjn0vvnmcvjppkn</string>
		</array>
	</dict>
</array>
<!-- End of the Google Sign-in Section -->
```

## Usage

### Import the package
To use this plugin, follow the [plugin installation instructions](https://pub.dartlang.org/packages/google_sign_in#pub-pkg-tab-installing).

### Use the plugin
Add the following import to your Dart code:

```
import 'package:google_sign_in/google_sign_in.dart';
```

Initialize GoogleSignIn with the scopes you want:

```
GoogleSignIn _googleSignIn = new GoogleSignIn(
  scopes: [
    'email',
    'https://www.googleapis.com/auth/contacts.readonly',
  ],
);
```

You can now use the `GoogleSignIn` class to authenticate in your Dart code, e.g. 

```
Future<Null> _handleSignIn() async {
  try {
    await _googleSignIn.signIn();
  } catch (error) {
    print(error);
  }
}
```

## Example

Find the example wiring in the [Google sign-in example application](https://github.com/flutter/plugins/blob/master/packages/google_sign_in/example/lib/main.dart).

## API details

See the [google_sign_in.dart](https://github.com/flutter/plugins/blob/master/packages/google_sign_in/lib/google_sign_in.dart) for more API details.

## Issues and feedback

Please file [issues](https://github.com/flutter/flutter/issues/new)
to send feedback or report a bug. Thank you!
