cmake_minimum_required(VERSION 3.20.0)

set(MACOSX_BUNDLE_GUI_IDENTIFIER "me.cjoftheweb.objcpptest")
set(MACOSX_DEPLOYMENT_TARGET 11.3)

project(objcpptest LANGUAGES CXX OBJCXX)

set(APP_SOURCE_FILES src/main.mm)
set(APP_STORYBOARDS res/Main.storyboard)

add_executable(objcpptest MACOSX_BUNDLE
  ${APP_SOURCE_FILES}
  ${APP_STORYBOARDS})
target_link_libraries(objcpptest
  "-framework Foundation"
  "-framework AppKit"
  "-framework Cocoa")

set_property(TARGET objcpptest APPEND_STRING PROPERTY
  COMPILE_FLAGS "-fobjc-arc")
set_target_properties(objcpptest PROPERTIES
  MACOSX_BUNDLE_INFO_PLIST ${CMAKE_CURRENT_SOURCE_DIR}/Info.plist
  MACOSX_BUNDLE_GUI_IDENTIFIER ${MACOSX_BUNDLE_GUI_IDENTIFIER}
  MACOSX_DEPLOYMENT_TARGET ${MACOSX_DEPLOYMENT_TARGET}
  XCODE_ATTRIBUTE_PRODUCT_BUNDLE_IDENTIFIER ${MACOSX_BUNDLE_GUI_IDENTIFIER}
  RESOURCE ${APP_STORYBOARDS})
