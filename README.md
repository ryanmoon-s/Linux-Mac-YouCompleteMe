# Linux-Mac-YouCompleteMe
**在linux和mac上使用YouCompleteMe**

安装YouCompleteMe的时候或多或少遇到一些问题  
大多是因为网络问题，YCM的thrid_party下载不下来，我将它们放在了自己的gitee仓库，方便下载   

<br/>

## Linux-Mac通用

**一、安装一些依赖，这是ubuntu，其它系统参照它**  
sudo apt-get install cmake  
sudo apt-get install llvm  
sudo apt-get install clang  
sudo apt-get install python3  
sudo apt-get install git  

**二、用Vundle管理ycm**  
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim  

**三、克隆ycm仓库**  
cd ~/.vim/bundle  
git clone  https://gitee.com/ryanmoon/YouCompleteMe.git  

**四、克隆最难下载的核心组件**  
cd ~/.vim/bundle/YouCompleteMe/third_party  
git clone https://gitee.com/ryanmoon/ycmd.git  

**五、编译ycm**  
cd ~/.vim/bundle/YouCompleteMe  
./install.sh --clang-completer --system-libclang    
(遇到缺少组件、版本过低，就apt-get、yum安装，安装不了就下载手动编译)
./install.py  

**六、使Vundle管理ycm：**  
vi ~/.vimrc  添加：
```powershell
set rtp+=~/.vim/bundle/Vundle.vim  
call vundle#begin()  
Plugin 'VundleVim/Vundle.vim'  
Plugin 'ycm-core/YouCompleteMe'  
call vundle#end()  
```

**七、配置ycm**  
vi ~/.vim    
参考：https://github.com/ryanmoon-s/VIM-Config    
将ycm相关的内容拷贝进此文件    

**八、使用ycm**  
将 ~/.vim/bundle/YouCompleteMe/.ycm_extra_conf.py 拷贝到项目目录下，增加下面的内容:
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
        '/usr/include/c++/9',
        ],
    }
#根据自己的语言配：c/c++
#-isystem表示头路径，后面紧跟一行头的搜索路径
```
