cmake_minimum_required(VERSION 3.24)

project(Test LANGUAGES CXX)

include(FetchContent)
FetchContent_Declare(
    Corrosion
    GIT_REPOSITORY https://github.com/corrosion-rs/corrosion.git
    GIT_TAG v0.3.2
)
FetchContent_MakeAvailable(Corrosion)

corrosion_import_crate(MANIFEST_PATH "${CMAKE_CURRENT_SOURCE_DIR}/Cargo.toml" CRATES corrosion-bug )

install(FILES $<TARGET_FILE:corrosion-bug-shared> TYPE LIB)
