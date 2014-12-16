# xmledit-cookbook

This cookbook allows incremental editing of XML files. You must include the
default recipe to ensure nokogiri and its dependencies are installed using the
upstream community xml cookbook.

Specifically, this library cookbooks offers a resource and provider that can be
called by the name `xml_edit`. This resource accepts XPath expressions and will
perform the expected action on the very first node found.

## Important notes

- If no XML nodes match the XPath expression, no actions will be performed. If a file cannot be found, this provider will raise an error by virtue of `::File` raising an error.

- This cookbook attempts to sidestep resource cloning issues by forcing the resource name to be something other than a path to a file to edit. This allows you to perform multiple edits to the same file by giving the resources unique names and providing the same path attribute value.

## Supported actions

|name|description|
|----|:-----------:|
|update|replaces a target node (and all children) with a new fragment|
|insert|appends a new XML fragment to a parent target node|
|remove|remove gets rid of a target node|

## Supported attributes

These have no default values, and will cause a no-op if they are not specified or don't match a valid file or target.

|name|required|description|
|----|:------:|:-----------:|
|path|true|path to the XML file to edit|
|target|true|an xpath expression for the target node or parent of the target node (see actions above)|
|fragment|true|a string that will be parsed into an XML fragment, for actions that add or update|

## TODO

 - Add an attribute for forcing an error when an xpath expr doesn't match

# License

```
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
```