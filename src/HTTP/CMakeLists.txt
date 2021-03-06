
cmake_minimum_required (VERSION 2.6)
project (Cuberite)

include_directories ("${PROJECT_SOURCE_DIR}/../")

SET (SRCS
	EnvelopeParser.cpp
	HTTPFormParser.cpp
	HTTPMessage.cpp
	HTTPMessageParser.cpp
	HTTPServer.cpp
	HTTPServerConnection.cpp
	MultipartParser.cpp
	NameValueParser.cpp
	SslHTTPServerConnection.cpp
	TransferEncodingParser.cpp
	UrlParser.cpp
)

SET (HDRS
	EnvelopeParser.h
	HTTPFormParser.h
	HTTPMessage.h
	HTTPMessageParser.h
	HTTPServer.h
	HTTPServerConnection.h
	MultipartParser.h
	NameValueParser.h
	SslHTTPServerConnection.h
	TransferEncodingParser.h
	UrlParser.h
)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
	set_source_files_properties(HTTPServer.cpp PROPERTIES COMPILE_FLAGS "-Wno-error=global-constructors ")
	set_source_files_properties(HTTPServerConnection.cpp PROPERTIES COMPILE_FLAGS "-Wno-error=switch-enum")
	set_source_files_properties(HTTPMessage.cpp PROPERTIES COMPILE_FLAGS "-Wno-error=tautological-compare")
endif()

if(NOT MSVC)
	add_library(HTTPServer ${SRCS} ${HDRS})
endif()
