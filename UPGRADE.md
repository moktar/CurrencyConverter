# CurrencyConverter - Upgrade Guide

## What's Been Updated (v2.0)

### Build Tools & Gradle
- ✅ Android Gradle Plugin: 3.3.0 → 8.1.4
- ✅ Target SDK: 28 → 34 (Android 14)
- ✅ Minimum SDK: 14 → 21 (Android 5.0 Lollipop)
- ✅ Java Compatibility: Now Java 11
- ✅ Gradle: Updated to use latest Kotlin plugin (1.9.0)

### Dependencies
- ✅ Support Library → **AndroidX Migration Complete**
  - `com.android.support:appcompat-v7:28.0.0` → `androidx.appcompat:appcompat:1.6.1`
  - `com.android.support.constraint:constraint-layout` → `androidx.constraintlayout:constraintlayout:2.1.4`
- ✅ OkHttp: 3.12.1 → 4.11.0 (security patches included)
- ✅ Testing: Updated to AndroidX test libraries
  - JUnit: 4.12 → 4.13.2
  - Test Runner: 1.0.2 → 1.5.2
  - Espresso: 3.0.2 → 3.5.1

### Repository Changes
- ✅ Removed deprecated JCenter → Using Maven Central only
- ✅ Added R8 code shrinking support
- ✅ Parallel Gradle builds enabled for faster compilation
- ✅ Jetifier enabled for library compatibility

### Code Changes Required

#### If you have Activities/Fragments:
Replace support imports:
```diff
- import android.support.v7.app.AppCompatActivity;
+ import androidx.appcompat.app.AppCompatActivity;

- import android.support.v4.app.Fragment;
+ import androidx.fragment.app.Fragment;
```

#### If you use Menu inflation:
```diff
- import android.support.v4.view.MenuItemCompat;
+ import androidx.core.view.MenuItemCompat;
```

#### AndroidManifest.xml
If your project extends AppCompatActivity, no changes needed (AndroidX handles it).

## Migration Steps

1. **Build the project:**
   ```bash
   ./gradlew clean build
   ```

2. **If IDE prompts for migrations:**
   - Accept AndroidX migration in Android Studio if prompted

3. **Run tests:**
   ```bash
   ./gradlew test
   ```

4. **Update version in your app:**
   - Bump version code and name in build.gradle files

## Compatibility Notes

- **Minimum API Level**: Now 21 (was 14)
- **Target API Level**: 34 (Android 14)
- **Java Version**: 11+ required for compilation
- **Kotlin Support**: Now available in the project

## Next Steps

Consider:
1. Adding Kotlin support for new features
2. Implementing Jetpack libraries (Room, LiveData, etc.)
3. Adding GitHub Actions CI/CD pipeline
4. Publishing updated version to JitPack
5. Adding ProGuard/R8 optimization rules

## Breaking Changes

⚠️ **API Level Requirement**: Apps using this library must target API 34 and have minSdkVersion >= 21

## Support

For issues during migration, check:
- [AndroidX Migration Guide](https://developer.android.com/jetpack/androidx/migrate)
- [OkHttp Upgrade Guide](https://square.github.io/okhttp/changelog/)
