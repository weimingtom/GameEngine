PROJECT(LineTriangle)
INCLUDE(CollectSrcs)
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/Include)
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR})
INCLUDE_DIRECTORIES($ENV{BOOST_INCLUDE})
#INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})

SET(LineTriangle_SUBDIRS )

GET_SRCS(LineTriangle_SRCLISTS LineTriangle_SUBDIRS)
LINK_DIRECTORIES(${CMAKE_BINARY_DIR}/Src/Common)
LINK_DIRECTORIES(${CMAKE_BINARY_DIR}/Src/Math)
LINK_DIRECTORIES(${CMAKE_BINARY_DIR}/Src/Graphic)
LINK_DIRECTORIES(${CMAKE_BINARY_DIR}/Src/Application)
LINK_DIRECTORIES($ENV{BOOST_LIB})

#MESSAGE(STATUS ${CMAKE_BINARY_DIR}/Src/Common)
#MESSAGE(STATUS ${CMAKE_BINARY_DIR}/Src/Math)
#MESSAGE(STATUS ${CMAKE_BINARY_DIR}/Src/Graphic)
#MESSAGE(STATUS ${CMAKE_BINARY_DIR}/Src/Application)

ADD_EXECUTABLE(LineTriangle ${LineTriangle_SRCLISTS})

TARGET_LINK_LIBRARIES(LineTriangle boost_system)
TARGET_LINK_LIBRARIES(LineTriangle boost_thread)
TARGET_LINK_LIBRARIES(LineTriangle boost_date_time)
TARGET_LINK_LIBRARIES(LineTriangle pthread)
TARGET_LINK_LIBRARIES(LineTriangle Common)
TARGET_LINK_LIBRARIES(LineTriangle Math)
TARGET_LINK_LIBRARIES(LineTriangle Graphic)
TARGET_LINK_LIBRARIES(LineTriangle Application)

#install configure
INSTALL(TARGETS LineTriangle
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib)


