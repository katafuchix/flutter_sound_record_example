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
      config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [
          '$(inherited)',
          'PERMISSION_CAMERA=1',
          'PERMISSION_MICROPHONE=1',
          'PERMISSION_SPEECH_RECOGNIZER=1',
       ]
    end
  end
end
```


