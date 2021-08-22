# Linux-Mac-YouCompleteMe

A document that teaches how to install youcompleteme in linux and mac systems  
\- 一个教如何在linux和mac系统上使用youcompleteme的文档 -

大家在安装YouCompleteMe的时候或多或少遇到一些问题  
大多是因为网络问题，YCM的thrid_party下载不下来，我将它们放在了自己的gitee仓库，方便下载 
下面教大家如何正确安装YCM 

<br/>

## Linux-Mac通用

**安装一些依赖，这是ubuntu，其它系统参照它**  
sudo apt-get install cmake  
sudo apt-get install llvm  
sudo apt-get install clang  
sudo apt-get install python3  
sudo apt-get install git  

**用Vundle管理ycm**
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim  

**克隆ycm仓库**
cd ~/.vim/bundle  
git clone  https://gitee.com/ryanmoon/YouCompleteMe.git  

**克隆最难下载的核心组件**
cd ~/.vim/bundle/YouCompleteMe/third_party  
git clone https://gitee.com/ryanmoon/ycmd.git  

**安装ycm**
cd ~/.vim/bundle/YouCompleteMe  
./install.sh --clang-completer --system-libclang  
如果遇到下载不下来的git链接，去gitee上面搜索并clone  

**使用ycm**
将 ~/.vim/bundle/YouCompleteMe/.ycm_extra_conf.py 拷贝到项目目录下，增加下面的内容，头文件等

```python
def Settings( **kwargs ):
    return {
        'flags': [
        'c++',
        '-std=c++11',
        '-Wall',
        '-Wextra',
        '-Werror',
        '-isystem',
        '/usr/include/',
        '-isystem',
        './include',
        ],
    }

#根据自己的语言配：c/c++
#-isystem表示头路径，后面紧跟一行头的搜索路径
```

<br/>

**使Vundle管理ycm：**

vi .vimrc  添加： 

```powershell
set rtp+=~/.vim/bundle/Vundle.vim  
call vundle#begin()  
Plugin 'VundleVim/Vundle.vim'  
Plugin 'ycm-core/YouCompleteMe'  
call vundle#end()  
```
