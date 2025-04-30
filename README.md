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
│
│   └── tv
└── media
    ├── movies
    └── tv
```