# Media Library Asset Synchronization Script

A `bash` script that processes a media library folder structure and scans for image assets to associate with each media (e.g. poster, title card).

## Contents

* [Requirements](#requirements)

## Requirements

The script expects a standard, well-organized file and folder structure that follows what has been established by [TRaSH Guides](https://trash-guides.info/File-and-Folder-Structure/). The basic principle is that you organize your media assets (images) either manually or via an automated process, and then the script will automate the process of ensuring your existing media library is using the assets you have provided.

### Example Folder Structure
```data
├── assets
│   ├── movies
│   │   ├── Frozen (2013) {tmdb-109445}
│   │   │   └── cover.png
│   │   ├── Shrek (2001) {tmdb-808}
│   │   │   └── poster.png
│   │   └── The Lego Movie (2014) {tmdb-137106}
│   │       └── poster.jpg
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
│       └── Home Improvement (1991) {tmdb-1558}
│           ├── Season 01
│           │   ├── S01E01.jpg
│           │   ├── S01E02.jpg
│           │   ├── ...
│           │   ├── S01E23.jpg
│           │   └── S01E24.jpg
│           ├── Season 02
│           │   ├── S02E01.jpg
│           │   ├── S02E02.jpg
│           │   ├── ...
│           │   ├── S01E23.jpg
│           │   └── S01E24.jpg
│           ├── Season 01.jpg
│           ├── Season 02.jpg
│           └── show.jpg
└── media
    ├── movies
    └── tv
```