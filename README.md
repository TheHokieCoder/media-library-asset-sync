# Media Library Asset Synchronization Script

A `bash` script that processes a media library folder structure and scans for local media assets to associate with each media (e.g. poster, title card). The script largely, if not exclusively, processes the local media assets to work with [Plex Media Server](https://www.plex.tv/) and its media scanning agents.

## Contents

* [Requirements](#requirements)

## Requirements

The script expects a standard, well-organized file and folder structure that follows what has been established by [TRaSH Guides](https://trash-guides.info/File-and-Folder-Structure/). The basic principle is that you organize your local media assets either manually or via an automated process, and then the script will automate the process of ensuring your existing media library is using the local media assets you have provided and will be picked up by Plex Media Server's scanning agents.

### Core Folder structure
```
data
├── assets
│   ├── movies
│   └── tv
└── media
    ├── movies
    └── tv
```

The `assets` and `media` folders *must* be on the same partition as the local media asset files will be hardlinked to their respective location in the `media` folder structure to prevent duplicating files and wasting storage space. (**NOTE**: a future improvement may provide an option to copy files instead of relying on hard links)

In the following example folder structure, the `assets` structure demonstrates the expected layout for organizing your local media assets for movies and TV shows. The `media` structure is example starting with no local media assets (i.e. a clean slate).

### Example Starting Folder Structure
```
data
├── assets
│   ├── movies
│   │   ├── Frozen (2013) {tmdb-109445}
│   │   │   └── cover.png
│   │   ├── Shrek (2001) {tmdb-808}
│   │   │   ├── poster.png
│   │   │   └── poster-2.png
│   │   ├── The Lego Movie (2014) {tmdb-137106}
│   │   │   ├── fanart.png
│   │   │   └── poster.jpg
│   │   └── &hellip;
│   └── tv
│       ├── Friends (1997) {tmdb-1668}
│       │   ├── Season 00
│       │   │   └── S00E01.jpg
│       │   ├── Season 01
│       │   │   ├── s01e01.jpg
│       │   │   ├── s01e02.jpg
│       │   │   ├── ...
│       │   │   ├── s01e23.jpg
│       │   │   └── s01e24.jpg
│       │   ├── Season 02
│       │   │   ├── S02E01.png
│       │   │   ├── S02E02.png
│       │   │   ├── ...
│       │   │   ├── S01E23.png
│       │   │   └── S01E24.png
│       │   ├── Season 00.jpg
│       │   ├── Season 01.jpg
│       │   ├── Season 02.jpg
│       │   └── show.png
│       ├── Home Improvement (1991) {tmdb-1558}
│       │   ├── Season 01
│       │   │   ├── S01E01.jpg
│       │   │   ├── S01E02.jpg
│       │   │   ├── ...
│       │   │   ├── S01E23.jpg
│       │   │   └── S01E24.jpg
│       │   ├── Season 02
│       │   │   ├── S02E01.jpg
│       │   │   ├── S02E02.jpg
│       │   │   ├── ...
│       │   │   ├── S01E23.jpg
│       │   │   └── S01E24.jpg
│       │   ├── Season 01.jpg
│       │   ├── Season 02.jpg
│       │   └── show.jpg
│       └── ...
├── media
│   ├── movies
│   │   ├── Frozen (2013) {tmdb-109445}
│   │   │   └── Frozen (2013).mkv
│   │   ├── Shrek (2001) {tmdb-808}
│   │   │   └── Shrek (2001).mkv
│   │   ├── The Lego Movie (2014) {tmdb-137106}
│   │   │   └── The Lego Movie (2014).mkv
│   │   └── ...
│   └── tv
│       ├── Friends (1997) {tmdb-1668}
│       │   ├── Season 00
│       │   │   └── Friends.1997.S00E01.mkv
│       │   ├── Season 01
│       │   │   ├── Friends.1997.S01E01.mkv
│       │   │   ├── Friends.1997.S01E02.mkv
│       │   │   ├── ...
│       │   │   ├── Friends.1997.S01E23.mkv
│       │   │   └── Friends.1997.S01E24.mkv
│       │   └── Season 02
│       │       ├── Friends.1997.S02E01.mkv
│       │       ├── Friends.1997.S02E02.mkv
│       │       ├── ...
│       │       ├── Friends.1997.S02E23.mkv
│       │       └── Friends.1997.S02E24.mkv
│       ├── Home Improvement (1991) {tmdb-1558}
│       │   ├── Season 01
│       │   │   ├── Home Improvement (1991) S01E01.mkv
│       │   │   ├── Home Improvement (1991) S01E02.mkv
│       │   │   ├── ...
│       │   │   ├── Home Improvement (1991) S01E23.mkv
│       │   │   └── Home Improvement (1991) S01E24.mkv
│       │   └── Season 02
│       │       ├── Home Improvement (1991) S02E01.mkv
│       │       ├── Home Improvement (1991) S02E02.mkv
│       │       ├── ...
│       │       ├── Home Improvement (1991) S02E23.mkv
│       │       └── Home Improvement (1991) S02E24.mkv
│       └── ...
└── ...
```