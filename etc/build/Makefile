# This is the entrypoint of the bblfsh make SDK, the SDK should be stored at
# `sdklocation`, generated executing `bblfsh-sdk prepare-build`. Many different
# vars as `LANGUAGE` are required, this variables are extracting from the
# `manifest.toml` at the root and the project translating it to a make include
# at `manifest` using `bblfsh-sdk manifest` tool.

location = $(shell pwd)
sdklocation = $(location)/.sdk
manifest = $(sdklocation)/make/manifest.mk
tmplocation = $(sdklocation)/tmp
$(shell mkdir -p $(tmplocation))

bblfsh-sdk := $(shell command -v bblfsh-sdk 2> /dev/null)
ifdef bblfsh-sdk
    $(shell $(bblfsh-sdk) manifest --print-env > $(manifest))
endif

include $(sdklocation)/make/manifest.mk
include $(sdklocation)/make/functions.mk
include $(sdklocation)/make/bootstrap.mk
include $(sdklocation)/make/rules.mk