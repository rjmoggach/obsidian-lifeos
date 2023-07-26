# Obsidian Periodic PARA

- This is a plugin for [LifeOS](https://quanru.github.io/2023/07/08/Building%20my%20second%20brain%20%F0%9F%A7%A0%20with%20Obsidian/), which assist in practicing the PARA system with periodic notes.
- You can download the [LifeOS-example](https://github.com/quanru/obsidian-example-LifeOS) to experience it.

## Installation

> [Dataview](https://github.com/blacksmithgu/obsidian-dataview) is required, please install it first.

#### BRAT
Periodic PARA has not been available in the Obsidian community plugin browser, but I already submitted it for [review](https://github.com/obsidianmd/obsidian-releases/pull/2117). You can install it by [BRAT](https://github.com/TfTHacker/obsidian42-brat).

#### Manual
Go to the [releases](https://github.com/quanru/obsidian-periodic-para/releases) and download the latest `main.js` and `manifest.json` files. Create a folder called `periodic-para` inside `.obsidian/plugins` and place both files in it.

## Settings

|Setting|Description|
|---|---|
|Periodic Notes Folder| Default is 'PeriodicNotes', Set a folder for periodic notes. The format of daily, weekly, monthly, quarterly, and yearly notes in the directory must meet the following requirements: YYYY-MM-DD、YYYY-Www、YYYY-MM、YYYY-Qq |
|Projects Folder      | Default is '1. Projects', Set a folder where the PARA project is located, each subdirectory is a project, and each project must have a [XXX.]README.md file as the project index |
|Areas Folder         | Default is '2. Areas', Set a folder where the PARA area is located, each subdirectory is a area, and each area must have a [XXX.]README.md file as the area index |
|Resources Folder     | Default is '3. Resources', Set a folder where the PARA resource is located, each subdirectory is a resource, and each resource must have a [XXX.]README.md file as the resource index |
|Archives Folder      | Default is '4. Archives', Set a folder where the PARA archive is located, each subdirectory is a archive, and each archive must have a [XXX.]README.md file as the archive index |
|Project List Header  | Default is 'Project List', Set the title of the module in which the project snapshots are located in daily notes to collect the projects experienced in the current period in the weekly, monthly, quarterly, and yearly notes |
|Area List Header     | Default is 'First Things Dimension', Set the title of the module in which the area snapshots are located in quarterly notes to collect the areas experienced in the current period in the yearly notes |
|Habit List Header    | Default is 'Habit', Set the title of the module in daily notes where the habit is located, and the task query view will ignore tasks under that title |

## Usage

### query code block

Periodic PARA works by writing markdown code block, which query project, area, task list according to the date parsed from current filename, and query task, bullet, project, area, resource, archive list according to the tags parsed from frontmatter.

#### query by time

Time scope is parsed from current file name, for example:

- 2023-01-01.md // Only 1 January is included
- 2023-W21.md // Every day of week 21
- 2023-06.md // Every day and every week of June
- 2023-Q3.md // Every day, every week, every month of Quarter 3
- 2023.md // Every day, every week, every month, every quarter of 2023

~~~markdown
```PeriodicPARA
TaskDoneListByTime
```
~~~


~~~markdown
```PeriodicPARA
TaskRecordListByTime
```
~~~


~~~markdown
```PeriodicPARA
ProjectListByTime
```
~~~

~~~markdown
```PeriodicPARA
AreaListByTime
```
~~~

#### query by tag

Tags is parsed from the frontmatter of current file, for example:

~~~markdown
---
tags: 
- x-project
---
~~~

The following code block would use x-project as the tag for the query.

~~~markdown
```PeriodicPARA
TaskListByTag
```
~~~

~~~markdown
```PeriodicPARA
BulletListByTag
```
~~~

~~~markdown
```PeriodicPARA
ProjectListByTag
```
~~~

~~~markdown
```PeriodicPARA
AreaListByTag
```
~~~

~~~markdown
```PeriodicPARA
ResourceListByTag
```
~~~

~~~markdown
```PeriodicPARA
ArchiveListByTag
```
~~~

#### query para by folder

~~~markdown
```PeriodicPARA
ProjectListByFolder
```
~~~

~~~markdown
```PeriodicPARA
AreaListByFolder
```
~~~

~~~markdown
```PeriodicPARA
ResourceListByFolder
```
~~~

~~~markdown
```PeriodicPARA
ArchiveListByFolder
```
~~~


### [templater](https://github.com/SilentVoid13/Templater) helpers

#### Generate list

Generate a list of README.md snapshots in the specified directory.

~~~markdown
<% PeriodicPARA.Project.snapshot() %>
<% PeriodicPARA.Area.snapshot() %>
<% PeriodicPARA.Resource.snapshot() %>
<% PeriodicPARA.Archive.snapshot() %>
~~~

For example:

~~~markdown
<% PeriodicPARA.Project.snapshot() %>
~~~

to

~~~markdown
1. [[1. Projects/x-project/README|x-project]]
2. [[1. Projects/y-project/README|y-project]]
~~~

## example

![](assets/periodic-para-plugin-en.png)

![](assets/periodic-para-plugin.png)


## next
- [x] Supports custom directories
  - PARA directories
  - Periodic directories
- [x] Support *ListByTag(ProjectListByTag, AreaListByTag, ResourceListByTag, ArchiveListByTag)
