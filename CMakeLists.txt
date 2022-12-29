cmake_minimum_required(VERSION 3.0)
project(HelloBoost)
set(Boost_USE_STATIC_LIBS OFF) 
set(Boost_USE_MULTITHREADED ON)  
set(Boost_USE_STATIC_RUNTIME OFF)
set(Boost_NO_SYSTEM_PATHS TRUE) 

if (Boost_NO_SYSTEM_PATHS)
  set(BOOST_ROOT "/usr")
  set(BOOST_INCLUDE_DIRS "${BOOST_ROOT}/include")
  set(BOOST_LIBRARY_DIRS "${BOOST_ROOT}/lib")
endif (Boost_NO_SYSTEM_PATHS)

#find_package(Boost COMPONENTS regex date_time system filesystem thread graph program_options) 

#find_package(Boost REQUIRED regex date_time system filesystem thread graph program_options)
#find_package(Boost COMPONENTS program_options REQUIRED)

find_package(Boost 1.81.0 COMPONENTS filesystem regex) 

if(Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIRS}) 
    add_executable(HelloBoost main.cpp) 
    target_link_libraries(HelloBoost Boost::filesystem Boost::regex)
endif(Boost_FOUND)
