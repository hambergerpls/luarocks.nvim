# Rocks.nvim

`rocks.nvim` is a Neovim plugin designed to streamline the installation of LuaRocks packages directly within Neovim. It simplifies the process of managing Lua dependencies, ensuring a hassle-free experience for Neovim users.

## Requirements

`rocks.nvim` has minimal requirements to ensure a smooth installation process. The primary requirement is having Python3 available in your system's PATH. It's important to note that Python3 is utilized solely for the installation of the `luarocks` tool and is not integrated into Neovim itself.

## Usage

### Lazy.nvim Integration

For users employing the Lazy.nvim plugin manager, effortlessly integrate `rocks.nvim` into your configuration by adding the following lines:

```lua
{
  "camspiers/rocks",
  dependencies = {
    "rcarriga/nvim-notify", -- Optional dependency
  },
  opts = {
    rocks = { "fzy" } -- Specify LuaRocks packages to install
  }
}
```

This snippet not only installs the `rocks.nvim` plugin but also provides an option to include additional LuaRocks packages. The "fzy" package is specified as an example.

### Other Plugin Managers

For users utilizing other plugin managers, manual setup is required. Use the following code to initialize `rocks.nvim`:

```lua
require("rocks").setup({ rocks = { "fzy" } })
```

Adjust the `rocks` array to include the names of the LuaRocks packages you want to install.

## Optional Dependencies

If you want nicer notifications during installation, add `rcarriga/nvim-notify` as a dependency:

```lua
{
  "camspiers/rocks",
  dependencies = {
    "rcarriga/nvim-notify", -- Optional dependency
  },
  opts = {
    rocks = { "fzy" } -- Specify LuaRocks packages to install
  }
}
```

## Build Process

The `rocks.nvim` plugin includes a build process to ensure proper functionality. The build process involves the following steps:

1. **Checking Python3 Existence**: Ensures the presence of the external 'python3' command.

2. **Creating Python3 Virtual Environment**: Establishes a Python3 virtual environment for the plugin.

3. **Installing hererocks**: Installs the `hererocks` tool.

4. **Installing LuaJIT**: Installs LuaJIT, with additional configuration for macOS.

### Manual Build Trigger

You can manually trigger the build process using the following command inside the plugin root:

```bash
nvim -l build.lua
```

Executing this command initiates the complete build process, ensuring that all dependencies are properly installed. This manual trigger can be useful in scenarios where you want to ensure a fresh installation or troubleshoot any issues related to the build process.

Please note that the build process is automatically invoked during the setup phase, so manual triggering may be unnecessary in most cases.
