# nvim-treesitter-pairs

Create your own pair objects using tree-sitter queries!

## Installation

You can install nvim-treesitter-pairs with your favorite package manager, or using the default pack feature of Neovim!

### Using a package manager

If you are using vim-plug, put this in your init.vim file:

```vim
Plug 'nvim-treesitter/nvim-treesitter', {'do': ':TSUpdate'}
Plug 'theHamsta/nvim-treesitter-pairs'
```

## Configuration

Pairs are configured via `queries/<language>/pairs.scm` query files.

```lua
lua <<EOF
require'nvim-treesitter.configs'.setup {
  pairs = {
    enable = true,
    disable = {},
    highlight_pair_events = {}, -- e.g. {"CursorMoved"}, -- when to highlight the pairs, use {} to deactivate highlighting
    highlight_self = false, -- whether to highlight also the part of the pair under cursor (or only the partner)
    goto_right_end = false, -- whether to go to the end of the right partner or the beginning
    fallback_cmd_normal = "call matchit#Match_wrapper('',1,'n')", -- What command to issue when we can't find a pair (e.g. "normal! %")
    keymaps = {
      goto_partner = "<leader>%",
      delete_balanced = "X",
    },
    delete_balanced = {
      only_on_first_char = false, -- whether to trigger balanced delete when on first character of a pair
      fallback_cmd_normal = nil, -- fallback command when no pair found, can be nil
      longest_partner = false, -- whether to delete the longest or the shortest pair when multiple found.
                               -- E.g. whether to delete the angle bracket or whole tag in  <pair> </pair>
    }
  }
},
EOF
```

## Known Limitations

We hope we can fix them soon!

- Can only cycle through 2-element pairs
- Only works in normal mode
- Queries are not complete at the moment
- Does not support counts
- Support all things that matchit does
- Is tree-sitter really needed or should we just use mature vim plugins that use regexes?

Alternatives: https://github.com/andymass/vim-matchup added tree-sitter support for some languages. Thy can be configured via `matchup.scm`.

## Supported languages

<!--pairsinfo-->
<table>
<tr>
<td>astro</td><td> </td> </tr>
<tr>
<td>bash</td><td>👍</td> </tr>
<tr>
<td>beancount</td><td> </td> </tr>
<tr>
<td>bibtex</td><td> </td> </tr>
<tr>
<td>c</td><td>👍</td> </tr>
<tr>
<td>c_sharp</td><td>👍</td> </tr>
<tr>
<td>clojure</td><td>👍</td> </tr>
<tr>
<td>cmake</td><td> </td> </tr>
<tr>
<td>comment</td><td> </td> </tr>
<tr>
<td>commonlisp</td><td>👍</td> </tr>
<tr>
<td>cooklang</td><td> </td> </tr>
<tr>
<td>cpp</td><td>👍</td> </tr>
<tr>
<td>css</td><td>👍</td> </tr>
<tr>
<td>cuda</td><td> </td> </tr>
<tr>
<td>d</td><td> </td> </tr>
<tr>
<td>dart</td><td>👍</td> </tr>
<tr>
<td>devicetree</td><td> </td> </tr>
<tr>
<td>dockerfile</td><td> </td> </tr>
<tr>
<td>dot</td><td> </td> </tr>
<tr>
<td>eex</td><td> </td> </tr>
<tr>
<td>elixir</td><td> </td> </tr>
<tr>
<td>elm</td><td>👍</td> </tr>
<tr>
<td>elvish</td><td> </td> </tr>
<tr>
<td>erlang</td><td> </td> </tr>
<tr>
<td>fennel</td><td>👍</td> </tr>
<tr>
<td>fish</td><td> </td> </tr>
<tr>
<td>foam</td><td> </td> </tr>
<tr>
<td>fortran</td><td> </td> </tr>
<tr>
<td>fusion</td><td> </td> </tr>
<tr>
<td>Godot (gdscript)</td><td> </td> </tr>
<tr>
<td>gleam</td><td> </td> </tr>
<tr>
<td>Glimmer and Ember</td><td> </td> </tr>
<tr>
<td>glsl</td><td> </td> </tr>
<tr>
<td>go</td><td>👍</td> </tr>
<tr>
<td>Godot Resources (gdresource)</td><td> </td> </tr>
<tr>
<td>gomod</td><td> </td> </tr>
<tr>
<td>gowork</td><td> </td> </tr>
<tr>
<td>graphql</td><td>👍</td> </tr>
<tr>
<td>hack</td><td> </td> </tr>
<tr>
<td>haskell</td><td>👍</td> </tr>
<tr>
<td>hcl</td><td> </td> </tr>
<tr>
<td>heex</td><td> </td> </tr>
<tr>
<td>help</td><td> </td> </tr>
<tr>
<td>hjson</td><td> </td> </tr>
<tr>
<td>hocon</td><td> </td> </tr>
<tr>
<td>html</td><td>👍</td> </tr>
<tr>
<td>http</td><td> </td> </tr>
<tr>
<td>java</td><td>👍</td> </tr>
<tr>
<td>javascript</td><td>👍</td> </tr>
<tr>
<td>jsdoc</td><td> </td> </tr>
<tr>
<td>json</td><td>👍</td> </tr>
<tr>
<td>json5</td><td> </td> </tr>
<tr>
<td>JSON with comments</td><td> </td> </tr>
<tr>
<td>julia</td><td>👍</td> </tr>
<tr>
<td>kotlin</td><td> </td> </tr>
<tr>
<td>lalrpop</td><td> </td> </tr>
<tr>
<td>latex</td><td>👍</td> </tr>
<tr>
<td>ledger</td><td> </td> </tr>
<tr>
<td>llvm</td><td> </td> </tr>
<tr>
<td>lua</td><td>👍</td> </tr>
<tr>
<td>make</td><td> </td> </tr>
<tr>
<td>markdown</td><td> </td> </tr>
<tr>
<td>ninja</td><td> </td> </tr>
<tr>
<td>nix</td><td>👍</td> </tr>
<tr>
<td>norg</td><td> </td> </tr>
<tr>
<td>ocaml</td><td> </td> </tr>
<tr>
<td>ocaml_interface</td><td> </td> </tr>
<tr>
<td>ocamllex</td><td>👍</td> </tr>
<tr>
<td>pascal</td><td> </td> </tr>
<tr>
<td>perl</td><td> </td> </tr>
<tr>
<td>php</td><td>👍</td> </tr>
<tr>
<td>phpdoc</td><td> </td> </tr>
<tr>
<td>pioasm</td><td> </td> </tr>
<tr>
<td>prisma</td><td> </td> </tr>
<tr>
<td>pug</td><td> </td> </tr>
<tr>
<td>python</td><td>👍</td> </tr>
<tr>
<td>ql</td><td> </td> </tr>
<tr>
<td>Tree-sitter query language</td><td> </td> </tr>
<tr>
<td>r</td><td> </td> </tr>
<tr>
<td>rasi</td><td> </td> </tr>
<tr>
<td>regex</td><td> </td> </tr>
<tr>
<td>rego</td><td> </td> </tr>
<tr>
<td>rst</td><td> </td> </tr>
<tr>
<td>ruby</td><td> </td> </tr>
<tr>
<td>rust</td><td>👍</td> </tr>
<tr>
<td>scala</td><td> </td> </tr>
<tr>
<td>scheme</td><td> </td> </tr>
<tr>
<td>scss</td><td>👍</td> </tr>
<tr>
<td>slint</td><td> </td> </tr>
<tr>
<td>solidity</td><td> </td> </tr>
<tr>
<td>sparql</td><td> </td> </tr>
<tr>
<td>supercollider</td><td> </td> </tr>
<tr>
<td>surface</td><td> </td> </tr>
<tr>
<td>svelte</td><td>👍</td> </tr>
<tr>
<td>swift</td><td> </td> </tr>
<tr>
<td>teal</td><td> </td> </tr>
<tr>
<td>tlaplus</td><td> </td> </tr>
<tr>
<td>todotxt</td><td> </td> </tr>
<tr>
<td>toml</td><td>👍</td> </tr>
<tr>
<td>tsx</td><td> </td> </tr>
<tr>
<td>turtle</td><td> </td> </tr>
<tr>
<td>typescript</td><td>👍</td> </tr>
<tr>
<td>vala</td><td> </td> </tr>
<tr>
<td>verilog</td><td> </td> </tr>
<tr>
<td>vim</td><td> </td> </tr>
<tr>
<td>vue</td><td>👍</td> </tr>
<tr>
<td>wgsl</td><td> </td> </tr>
<tr>
<td>yaml</td><td> </td> </tr>
<tr>
<td>yang</td><td> </td> </tr>
<tr>
<td>zig</td><td> </td> </tr>
</table>
<!--pairsinfo-->
