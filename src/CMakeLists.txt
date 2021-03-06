include(hello_imgui_add_app)

execute_process(COMMAND bash -c ${CMAKE_CURRENT_LIST_DIR}/populate_assets.sh)

set(implot_dir ${CMAKE_CURRENT_LIST_DIR}/../external/implot)
set(textedit_dir ${CMAKE_CURRENT_LIST_DIR}/../external/ImGuiColorTextEdit)
set(fplus_dir ${CMAKE_CURRENT_LIST_DIR}/../external/FunctionalPlus/include)
set(imgui_markdown_dir ${CMAKE_CURRENT_LIST_DIR}/../external/imgui_markdown)

hello_imgui_add_app(implot_demo
    ImplotDemo.main.cpp
    LibrarySources.cpp
    LibrarySources.h
    ImGuiExt.cpp
    ImGuiExt.h
    MarkdownHelper.cpp
    MarkdownHelper.h
    HyperlinkHelper.cpp
    HyperlinkHelper.h
    ${implot_dir}/implot.h
    ${implot_dir}/implot.cpp
    ${implot_dir}/implot_demo.cpp
    ${textedit_dir}/TextEditor.h
    ${textedit_dir}/TextEditor.cpp
    )
target_include_directories(implot_demo PRIVATE
    ${implot_dir} ${textedit_dir} ${fplus_dir} ${imgui_markdown_dir}
)
