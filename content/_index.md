+++
title = "Crow Translate"
+++

Crow Translate is a simple and lightweight translator written in C++ / Qt that allows you to translate and speak text using Google, Yandex, Bing, LibreTranslate and Lingva translate API.

# Features

- Translate and speak text from screen or selection
- Support 125 different languages
- Low memory consumption (~20MB)
- Highly customizable shortcuts
- Command-line interface with rich options
- D-Bus API
- Available for Linux and Windows

# Installation

## Windows

🌐 Installer from the [Releases](https://github.com/crow-translate/crow-translate/releases/latest) page.

📦 [Scoop package](https://github.com/lukesampson/scoop-extras/blob/master/bucket/crow-translate.json)

```bash
sudo scoop install crow-translate -g
```

**Note:** Windows requires [Microsoft Visual C++ Redistributable 2019](https://support.microsoft.com/en-us/topic/the-latest-supported-visual-c-downloads-2647da03-1eea-4433-9aff-95f26a218cc0) to work.

## Linux

### Arch Linux, Manjaro, Chakra, etc

📦 [Stable version in AUR](https://aur.archlinux.org/packages/crow-translate)

```bash
git clone https://aur.archlinux.org/crow-translate.git
cd crow-translate
makepkg -si
```

📦 [Git version in AUR](https://aur.archlinux.org/packages/crow-translate-git)

```bash
git clone https://aur.archlinux.org/crow-translate-git.git
cd crow-translate-git
makepkg -si
```

📦 [Chaotic-AUR repository](https://lonewolf.pedrohlc.com/chaotic-aur)

```bash
sudo pacman -S crow-translate
```

### Ubuntu, Linux Mint, KDE Neon, etc

🌐 Package the [Releases](https://github.com/crow-translate/crow-translate/releases/latest) page.

📦 [Launchpad PPA](https://launchpad.net/~jonmagon/+archive/ubuntu/crow-translate)

```bash
sudo add-apt-repository ppa:jonmagon/crow-translate
sudo apt update
sudo apt install crow-translate
```

### Fedora

🌐 Package the [Releases](https://github.com/crow-translate/crow-translate/releases/latest) page.

📦 [Fedora Copr](https://copr.fedorainfracloud.org/coprs/carlis/crow-translate)

```bash
sudo dnf copr enable carlis/crow-translate
sudo dnf install crow-translate
```

### CentOS, RHEL

📦 [Fedora Copr](https://copr.fedorainfracloud.org/coprs/carlis/crow-translate)

```bash
sudo yum copr enable carlis/crow-translate
sudo yum install crow-translate
```

### Mageia 7

📦 [BlogDrake repository](http://ftp.blogdrake.net)

```bash
# With urpmi
sudo urpmi urpmi.addmedia --wget --distrib http://ftp.blogdrake.net/mageia/mageia7/x86_64 # Or i586
sudo urpmi crow-translate

# Or with dnf
sudo dnf config-manager --add-repo http://ftp.blogdrake.net/mageia/BDK.repo
sudo dnf install crow-translate
```

### openSUSE Tumbleweed

📦 [Tumbleweed repository](https://software.opensuse.org/package/crow-translate)

```bash
sudo zypper install crow-translate
```

### openSUSE Leap

📦 [Open Build Service](https://software.opensuse.org/package/crow-translate)

### Solus

📦 [Solus repository](https://dev.getsol.us/source/crow-translate)

```bash
sudo eopkg it crow-translate
```

### Flatpak

📦 [Flathub](https://flathub.org/apps/details/io.crow_translate.CrowTranslate)

```bash
flatpak install flathub io.crow_translate.CrowTranslate
```

**Note:** To make the application look native on a non-KDE desktop environment, you need to configure Qt applications styling. This can be done by using [qt5ct](https://github.com/RomanVolak/qt5ct) or [adwaita-qt5](https://github.com/FedoraQt/adwaita-qt) or [qtstyleplugins](https://github.com/qt/qtstyleplugins). Please check the appropriate installation guide for your distribution.

# Default keyboard shortcuts

You can change them in the settings. Some key sequences may not be available due to OS limitations.

Wayland does not support global shortcuts registration, but you can use [D-Bus](#d-bus-api) to bind actions in the system settings. For desktop environments that support [additional applications actions](https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#extra-actions) (KDE, for example) you will see them predefined in the system shortcut settings. You can also use them for X11 sessions, but you need to disable global shortcuts registration in the application settings to avoid conflicts.

## Global

| Key                                             | Description                        |
| ----------------------------------------------- | ---------------------------------- |
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>E</kbd> | Translate selected text            |
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>S</kbd> | Speak selected text                |
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>F</kbd> | Speak translation of selected text |
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>G</kbd> | Stop speaking                      |
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>C</kbd> | Show main window                   |
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>I</kbd> | Recognize text in screen area      |
| <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>O</kbd> | Translate text in screen area      |

## In main window

| Key                                               | Description                             |
| ------------------------------------------------- | --------------------------------------- |
| <kbd>Ctrl</kbd> + <kbd>Return</kbd>               | Translate                               |
| <kbd>Ctrl</kbd> + <kbd>R</kbd>                    | Swap languages                          |
| <kbd>Ctrl</kbd> + <kbd>Q</kbd>                    | Close window                            |
| <kbd>Ctrl</kbd> + <kbd>S</kbd>                    | Speak source / pause text speaking      |
| <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>S</kbd> | Speak translation / pause text speaking |
| <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>C</kbd> | Copy translation to clipboard           |

# CLI commands

The program also has a console interface.

**Usage:** `crow [options] text`

| Option                     | Description                                                                                                         |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `-h, --help`               | Display help                                                                                                        |
| `-v, --version`            | Display version information                                                                                         |
| `-c, --codes`              | Display language codes                                                                                              |
| `-s, --source <code>`      | Specify the source language (by default, engine will try to determine the language on its own)                      |
| `-t, --translation <code>` | Specify the translation language(s), splitted by '+' (by default, the system language is used)                      |
| `-l, --locale <code>`      | Specify the translator language (by default, the system language is used)                                           |
| `-e, --engine <engine>`    | Specify the translator engine ('google', 'yandex', 'bing', 'libretranslate' or 'lingva'), Google is used by default |
| `-p, --speak-translation`  | Speak the translation                                                                                               |
| `-u, --speak-source`       | Speak the source                                                                                                    |
| `-f, --file`               | Read source text from files. Arguments will be interpreted as file paths                                            |
| `-i, --stdin`              | Add stdin data to source text                                                                                       |
| `-a, --audio-only`         | Print text only for speaking when using `--speak-translation` or `--speak-source`                                   |
| `-b, --brief`              | Print only translations                                                                                             |
| `-j, --json`               | Print output formatted as JSON                                                                                      |

**Note:** If you do not pass startup arguments to the program, the GUI starts.

# D-Bus API

    io.crow_translate.CrowTranslate
    ├── /io/crow_translate/CrowTranslate/Ocr
    |   └── method void io.crow_translate.CrowTranslate.Ocr.setParameters(QVariantMap parameters);
    └── /io/crow_translate/CrowTranslate/MainWindow
        |   # Global shortcuts
        ├── method void io.crow_translate.CrowTranslate.MainWindow.translateSelection();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.speakSelection();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.speakTranslatedSelection();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.playPauseSpeaking();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.stopSpeaking();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.open();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.copyTranslatedSelection();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.recognizeScreenArea();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.translateScreenArea();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.delayedRecognizeScreenArea();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.delayedTranslateScreenArea();
        |   # Main window shortcuts
        ├── method void io.crow_translate.CrowTranslate.MainWindow.clearText();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.cancelOperation();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.swapLanguages();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.openSettings();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.setAutoTranslateEnabled(bool enabled);
        ├── method void io.crow_translate.CrowTranslate.MainWindow.copySourceText();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.copyTranslation();
        ├── method void io.crow_translate.CrowTranslate.MainWindow.copyAllTranslationInfo();
        └── method void io.crow_translate.CrowTranslate.MainWindow.quit();

For example, you can show main window using `dbus-send`:

```bash
dbus-send --type=method_call --dest=io.crow_translate.CrowTranslate /io/crow_translate/CrowTranslate/MainWindow io.crow_translate.CrowTranslate.MainWindow.open
```

Or via `qdbus`:

```bash
qdbus io.crow_translate.CrowTranslate /io/crow_translate/CrowTranslate/MainWindow io.crow_translate.CrowTranslate.MainWindow.open
# or shorter
qdbus io.crow_translate.CrowTranslate /io/crow_translate/CrowTranslate/MainWindow open
```
