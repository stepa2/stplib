# STPLib

```
hook .PreFileIncluded(filename: string, realm: "sv"|"sh"|"cl")
fn .GetRealmFromFilename(filename: string) -> "sv"|"sh"|"cl"
fn .IncludeFile(filename: string) -> file_return: ...|nil
fn .IncludeList(prefix: string, files: array(string))
fn .IncludeDir(dir: string, recursive: bool|nil=false)

fn .Error(parts: ...(any)) -- Unlike GMod Error(), this actually errors and halts execution

fn .CheckType(val: any|nil, valname: string, allowed_types: array(string)|string) -> val: any|nil

fn .RegisterType(name: string, {
    IsInstance: fn(value: any|nil) -> bool
})

fn .IsType(val: any|nil, type: string) -> bool
fn .ToString(val: any|nil, pretty_print: bool|nil = false) -> string

type .ClassIdent = string

# Returns metatable (can be made publicaly-available and inner constructor function (supposed to be local))
# Registers type with .RegisterType
# Each class in `parents` should be defined before this call
# If multiple parents are given, they are searched in given order 
fn .DefineClass(name: .ClassIdent, parents: array(.ClassIdent)) -> <metatable>, fn(inner_data: table(any,any)) -> <class 'name' instance>

# Never returns nil, can be called before .DefineClass(name, {...}) is called
fn .GetClassMeta(name: .ClassIdent) -> <metatable>

```