# flutter_sound_record_example

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
# flutter_sound_record_example


```
post_install do |installer|
  installer.pods_project.targets.each do |target|
    flutter_additional_ios_build_settings(target)
    target.build_configurations.each do |config|
      config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= []
      config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] << 'PERMISSION_MICROPHONE=1'
    end
  end
end
```

```
pb_release is defined in the pb_decode.h included at the top of GDTCCTUploadOperation.m
```

こんなエラーが出てダメな場合は

```
post_install do |installer|
  installer.pods_project.targets.each do |target|
    flutter_additional_ios_build_settings(target)
    target.build_configurations.each do |config|
      config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [  # コンパイラのビルド設定を定義
          '$(inherited)',
          'PERMISSION_CAMERA=1',
          'PERMISSION_MICROPHONE=1',
          'PERMISSION_SPEECH_RECOGNIZER=1',
       ]
    end
  end
end
```

$(inherited)は、既存の設定をそのまま継承するために使用されます。このようにすることで、Flutterや他のライブラリが設定したデフォルトの定義が保持されます。

'PERMISSION_CAMERA=1', 'PERMISSION_MICROPHONE=1', 'PERMISSION_SPEECH_RECOGNIZER=1'
これらは、それぞれの権限（カメラ、マイク、音声認識）の使用を有効化するためのプリプロセッサ定義です。permission_handlerパッケージを使用する際、これらの権限に対応するマクロを定義することで、各権限のリクエストが正常に動作するようになります。

具体的には、これらのマクロを定義することで、CocoaPodsを使用して依存関係をインストールした際に、アプリがこれらの機能を使用することを許可するための設定が有効化されます。これにより、マイクの利用許可ウィンドウが正しく表示されるようになったと考えられます。

このコードは、iOSアプリのビルド時にカメラ、マイク、音声認識の許可リクエストを適切に行うための設定を追加しています。特に、permission_handlerパッケージを使用する場合に、権限リクエストを適切に処理するために必要なプリプロセッサマクロを定義しています。

