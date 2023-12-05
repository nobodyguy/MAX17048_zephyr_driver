# SPDX-License-Identifier: Apache-2.0

# Point to this project's root directory.
set(MAX17048_DIR ${CMAKE_CURRENT_LIST_DIR} CACHE PATH "MAX17048 module root directory")

# Subdirectories
add_subdirectory(drivers)

# Include headers
zephyr_include_directories(drivers)