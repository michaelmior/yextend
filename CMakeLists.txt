cmake_minimum_required(VERSION 3.5)
project(yextend)

include_directories(${yextend_SOURCE_DIR} ${yextend_SOURCE_DIR}/libs)

find_package(BZip2 REQUIRED)
find_package(LibArchive REQUIRED)
find_package(OpenSSL REQUIRED)
find_package(ZLIB REQUIRED)

add_executable(yextend
  libs/json.hpp
  wrapper.cpp
  bayshore_content_scan.cpp
  libs/bayshore_file_type_detect.c
  main.cpp
  libs/zl.cpp
  libs/bayshore_yara_wrapper.c
  libs/bzl.cpp
  libs/pdf_parser.cpp
  libs/pdf_parser_helper.cpp
  libs/pdf.cpp
  libs/pdf_object.cpp
  libs/pdf_font.cpp
)

target_link_libraries(yextend
  BZip2::BZip2
  LibArchive::LibArchive
  ZLIB::ZLIB
  openssl::openssl

  pcrecpp
  uuid
  yara
)
