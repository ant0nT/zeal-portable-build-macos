# zeal-portable-build-macos
Instruction for zeal portable build for mac os. You can obtain it for macos sonoma x86_64 arch from the release page. If it will be requsts I'll build and upload for other macos versions, maybe except arm, cause I don't have any mac with m-chip.

1. Build qt6 from source following by the instruction (step 1-2): https://doc.qt.io/qt-6/macos-building.html. *It may take several hours with full cpu load.* Also you can find builded qt6 framework from the release page.

2. Install libarchive with brew

    brew install libarchive

4. Install cmake. https://cmake.org/download/ Will be great!

5. Clone zeal repository with git

6. Replace following strings in zeal-rep/src/app/CMakeLists.txt

    qt_add_executable(App WIN32
        main.cpp
        zeal.qrc
        ${App_RESOURCES}
    )

   to:

   qt_add_executable(App
        main.cpp
        zeal.qrc
        ${App_RESOURCES}
    )L

7. Configure zeal for building with CMake.app. Choose unix make generator. Set CMAKE_BUILD_TYPE to Release. CMAKE_INSTALL_PREFIX to any directory in your home. QT-DIR to /builded-qt/lib/cmake/QT6. QT6-DIR to  /builded-qt/lib/cmake/QT6. Check ZEAL_PORTABLE_BUILD. Check advanced options. Set LibArchive_INCLUDE_DIR to /libarchive-install-brew/include. Set LibArchive_LIBRARY to /libarchive-install-brew/lib/libarchive.dylib.
  
8. After successful configure, open terminal and change directory to zeal_cmake_build_path.
  
   cd /path/where_to_build_the_binaries/
     
9. Run cmake
  
       /Applications/CMake.app/Contents/bin/cmake --build .
      
10. Create Zeal.app bundle with cmake
  
       /Applications/CMake.app/Contents/bin/cmake --install .
         
11. Copy Zeal.app on other computer or directory for linking libs into bundle.
  
If your have any question, suggestion and e.t.c let me know. If will be requests I can detail this instruction.
