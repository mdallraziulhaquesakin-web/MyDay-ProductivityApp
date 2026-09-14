# MyDay - Productivity & Daily Note-Taking App

A complete Android app for productivity tracking, task management, and daily activity logging.

## Features

✅ **Dashboard** - Today's summary with tasks, completion percentage, and current time
✅ **Task Management** - Create, edit, delete tasks with priority, category, and reminders
✅ **Daily Notes** - Record activities with start/end times and categories
✅ **Tomorrow's Plan** - Pre-plan next day's tasks
✅ **Notifications** - Automatic reminders with action buttons
✅ **Calendar** - View tasks and activities by date
✅ **Weekly Summary** - Productivity stats and charts
✅ **Monthly Reports** - In-depth analytics and comparisons
✅ **Categories** - Customizable productivity categories
✅ **Search & History** - Browse and search previous activities
✅ **Dark/Light Mode** - Theme switching
✅ **Local Database** - Room Database for offline storage
✅ **Backup & Restore** - Export/import data as JSON

## Project Structure

```
MyDay/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/myday/
│   │   │   │   ├── MainActivity.kt
│   │   │   │   ├── ui/
│   │   │   │   │   ├── screens/
│   │   │   │   │   ├── components/
│   │   │   │   │   └── theme/
│   │   │   │   ├── database/
│   │   │   │   ├── models/
│   │   │   │   ├── repository/
│   │   │   │   ├── notifications/
│   │   │   │   └── utils/
│   │   │   ├── res/
│   │   │   │   ├── values/
│   │   │   │   ├── drawable/
│   │   │   │   └── layout/
│   │   │   └── AndroidManifest.xml
│   │   └── test/
│   └── build.gradle.kts
├── gradle/
│── build.gradle.kts
├── settings.gradle.kts
├── gradle.properties
└── README.md
```

## Installation & Setup

### Prerequisites
- Android Studio (latest version) or AndroidIDE
- Kotlin 1.8+
- Android SDK 24 or higher
- JDK 11 or higher

### Quick Start

1. **Extract the ZIP file**
   ```bash
   unzip MyDay-ProductivityApp.zip
   cd MyDay
   ```

2. **Open in Android Studio**
   - Launch Android Studio
   - Click "Open" → Select the extracted folder
   - Wait for Gradle sync to complete

3. **Or Open in AndroidIDE**
   - Launch AndroidIDE
   - File → Open Project → Select MyDay folder
   - Let Gradle sync automatically

4. **Build the Project**
   - Menu: Build → Make Project
   - Or press Ctrl+F9 (Windows/Linux) / Cmd+F9 (Mac)
   - Wait for build to complete

5. **Run on Emulator or Device**
   - Connect Android device (USB debugging enabled) or start emulator
   - Click "Run" → Select device
   - App will install and launch automatically

6. **Generate APK for Installation**
   - Build → Build Bundle(s) / APK(s) → Build APK(s)
   - APK location: `app/build/outputs/apk/debug/app-debug.apk`
   - Transfer to device and install via ADB:
     ```bash
     adb install app/build/outputs/apk/debug/app-debug.apk
     ```

## Usage Guide

### Dashboard
- View today's tasks, completion percentage, and current time
- Quick add task or note buttons
- Swipe to see tomorrow's plan
- Progress indicator for daily goals

### Create Task
- Tap "+" → Create Task
- Enter title, description, date, time
- Set priority (Low/Medium/High)
- Choose category
- Enable notifications
- Set repeat option (None/Daily/Weekly/Monthly)

### Daily Activities
- Record what you actually did today
- Add start time, end time, category
- Track productive hours by category
- View total time spent on activities

### View Calendar
- Select any date to see tasks and activities
- Color-coded productivity levels
- View completion percentage per day
- Navigate between months

### Weekly & Monthly Reports
- Automatic charts and statistics
- Category-wise breakdown
- Productivity trends
- Month-to-month comparisons

### Settings
- Theme (Dark/Light/System)
- Notification preferences
- Default reminder time
- Manage categories
- Backup & Restore data
- About app information

## Technologies Used

- **Language**: Kotlin
- **UI Framework**: Jetpack Compose + Material Design 3
- **Database**: Room Database (Local SQLite)
- **Architecture**: MVVM with Repository Pattern
- **Notifications**: Android WorkManager + NotificationManager
- **State Management**: ViewModel & LiveData
- **Charts**: Simple chart library for statistics

## Permissions Required

- `POST_NOTIFICATIONS` - Send notifications
- `SCHEDULE_EXACT_ALARM` - Exact alarm scheduling
- `READ_EXTERNAL_STORAGE` - Import backup files
- `WRITE_EXTERNAL_STORAGE` - Export backups
- `INTERNET` - Optional for future cloud features

## Database Schema

### Tasks Table
```
- id: Int (Primary Key)
- title: String
- description: String
- date: Long (milliseconds)
- startTime: Long (milliseconds)
- endTime: Long (milliseconds)
- priority: Int (1=Low, 2=Medium, 3=High)
- categoryId: Int
- isCompleted: Boolean
- reminder: Boolean
- reminderTime: Long
- repeatType: String (NONE, DAILY, WEEKLY, MONTHLY)
- createdAt: Long
```

### Activities Table
```
- id: Int (Primary Key)
- title: String
- description: String
- date: Long (milliseconds)
- startTime: Long (milliseconds)
- endTime: Long (milliseconds)
- categoryId: Int
- durationMinutes: Int
- createdAt: Long
```

### Categories Table
```
- id: Int (Primary Key)
- name: String
- color: Int (ARGB color)
- icon: String
```

## Notification System

- Background WorkManager jobs for scheduling reminders
- Notification channels for organized notifications
- Action buttons: Complete, Snooze (5/15/30 mins), Dismiss
- Works even when app is closed
- Respects device Do Not Disturb settings

## Data Backup & Restore

- **Export**: Settings → Backup → Export as JSON
- **Import**: Settings → Restore → Select JSON file
- Data includes all tasks, activities, categories, and settings
- Backups are stored in `/Downloads/MyDay_Backup_YYYY-MM-DD.json`

## Customization

### Add Custom Category
- Settings → Categories → Add New
- Set name and color
- Use in tasks and activities
- Edit or delete existing categories

### Change Theme
- Settings → Theme
- Light mode
- Dark mode
- System default

### Notification Settings
- Settings → Notifications → Enable/Disable
- Set default reminder time
- Choose notification sound
- Enable/disable vibration

## Troubleshooting

**App crashes on launch:**
- Clear app data: Settings → Apps → MyDay → Storage → Clear Data
- Delete app and reinstall
- Check Android version compatibility (min API 24)

**Notifications not working:**
- Check if notifications are enabled in app settings
- Enable notifications in system settings
- Ensure battery optimization is not blocking the app
- Check notification permission is granted
- Restart the app and device

**Database errors:**
- Backup your data first
- Clear app cache: Settings → Apps → MyDay → Storage → Clear Cache
- Clear app data and start fresh

**Gradle sync issues:**
- Update Android Studio to latest version
- Delete `.gradle` folder and sync again
- Check internet connection for downloading dependencies

**Build failures:**
- Ensure JDK 11+ is installed
- Check Android SDK is properly configured
- Update Gradle wrapper: `./gradlew wrapper --gradle-version=8.0`

## API Compatibility

- **Minimum SDK**: Android 7.0 (API 24)
- **Target SDK**: Android 14 (API 34)
- **Tested on**: Android 12, 13, 14
- **JVM Target**: 11

## File Descriptions

```
app/
├── build.gradle.kts          # App-level Gradle configuration
├── src/main/
│   ├── java/com/example/myday/
│   │   ├── MainActivity.kt    # Entry point activity
│   │   ├── ui/
│   │   │   ├── screens/       # Composable screens
│   │   │   ├── components/    # Reusable UI components
│   │   │   └── theme/         # Theme and colors
│   │   ├── database/          # Room database setup
│   │   ├── models/            # Data classes
│   │   ├── repository/        # Data access layer
│   │   ├── notifications/     # Notification handlers
│   │   └── utils/             # Utility functions
│   └── res/
│       ├── values/strings.xml # String resources
│       ├── drawable/          # Icons and drawables
│       └── values/colors.xml  # Color definitions
│   └── AndroidManifest.xml    # App manifest
build.gradle.kts              # Project-level Gradle
settings.gradle.kts           # Gradle settings
gradle.properties             # Gradle properties
```

## Future Enhancements

- ☐ Cloud synchronization
- ☐ Shared tasks with family/team
- ☐ Voice input for tasks
- ☐ AI-powered productivity suggestions
- ☐ Integration with calendar apps
- ☐ Export to PDF reports
- ☐ Widget support
- ☐ Habit tracking
- ☐ Pomodoro timer integration
- ☐ Social sharing of achievements

## License

MIT License - Free to use and modify

## Support & Contribution

For issues, feature requests, and contributions, visit the GitHub repository.

## Contact

For questions and feedback about MyDay, open an issue on GitHub.

---

**Version**: 1.0.0
**Last Updated**: September 2026
**Made with ❤️ for better productivity**
