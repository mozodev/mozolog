---
title: Mac OS X 베이그런트 박스 만들기
date: 2016-01-13
---

맥에서 개발하다보면 hombrew로 잘모르겠지만 필요한 것 같은 패키지들을 많이 설치해서 사용하게 됩니다. 
그러다보면 뒤죽박죽 아름다운 맥이 더렵혀져서 언젠가 날을 잡아 밀고 싶어집니다.
몇 번 이런 상황이 반복되다 보니, 아 베이그런트( [vagrant](http://vagrantup.com) ) 박스가 없을까 히다가
검색해보니 [Developing on OS X Inside Vagrant](http://spin.atomicobject.com/2015/11/17/vagrant-osx/) 이런 글을 찾아서 반가운 마음에 따라 해보기로 했습니다.

필자는 애플이 [맥오에스텐을 가상화해서 사용할 권리](http://robb.weblaws.org/2015/10/17/os-x-el-capitan-license-in-plain-english/)는 줬지만, 그 복사본을 공유할 권리를 준 건 아니라고 하면서 직접 만들어 쓰라고 그 과정을 적었더군요. 

## 1. 시작하기

어쨌든 OS X 베이그런트 박스를 만들기 위한 템플릿인 Tim Sutton 이란 분이 만든 [timsutton/osx-vm-templates](https://github.com/timsutton/osx-vm-templates) 을 활용하면 된다고 합니다. 팀은 vmware fusion을 추천했다고는 하지만 저도 필자와 마찬가지로 퍼포먼스가 뛰어난 건 아니지만 돌아가고 무료인 virtualbox를 사용하고 있습니다.

### 준비사항

* 엘카피탄 설치 앱 (앱스토어에서 내려받기)
* [timsutton/osx-vm-templates](https://github.com/timsutton/osx-vm-templates)
* [packer](https://packer.io), a tool for creating machine and container images for multiple platforms from a single source configuration.

## 2. 디스크 이미지 만들기

우선 앱스토어에서 받은 설치 앱에서 설치용 디스크 이미지를 추출해야 합니다.
깃헙 프로젝트를 클론한 후 `prepare_iso/prepare_iso.sh`를 실행하면 추출할 수 있습니다.

```
# cd to working directory
git clone https://github.com/timsutton/osx-vm-templates
cd osx-vm-templates/

# Preparing the ISO
sudo prepare_iso/prepare_iso.sh \
    -D DISABLE_REMOTE_MANAGEMENT \
    /Applications/Install\ OS\ X\ El\ Capitan.app/ \
    packer/
```

버추얼 박스의 경우 `-D DISABLE_REMOTE_MANAGEMENT` 옵션으로 원격 관리 기능을 끄지 않으면 freeze 증상이 있다고 합니다. 어쨌든 이렇게 실행하면 대략 10분인가? 시간이 꽤 걸립니다. 실행이 완료되면 다음과 같은 메시지가 나오는데
패커로 빌드하기 위해 md5 해시 값이 필요해서 복사해둡니다.

```
-- Fixing permissions..
-- Checksumming output image..
-- MD5: 19b575fb4266ff68219a512be61263db
-- Done. Built image is located at packer/OSX_InstallESD_10.11.1_15B42.dmg. Add this iso and its checksum to your template.
```

## 3. 베이그런트 박스 만들기

이제 패커를 사용해서 버추얼박스 인스턴스를 생성해서 베이스 박스로 만듭니다. 옵션이 몇 가지 있는데 gui 로그인 시 자동 로그인하는 것과 시스템 자동 업데이트를 끄는 옵션이 있습니다. 나머지는 기본으로 넣어줍니다. osx-vm-templates 프로젝트 리드미 문서에 보면 사용자 아이디 비번, 로고 등을 교체할 수 있는 옵션도 있는데 별로 쓸 일은 없을 것 같습니다.

```
_# 패커 설치
brew install packer

# 빌드
packer build -var iso_checksum=19b575fb4266ff68219a512be61263db \
    -var iso_url=./OSX_InstallESD_10.11.1_15B42.dmg \
    -only=virtualbox-iso \
    -var autologin=true \
    -var update_system=0 \
    ./template.json_
```

실행하면 실제로 버추얼박스 인스턴스를 생성해서 설치를 진행합니다. 엘카피탄 설치하는 시간이 꽤 깁니다. 담배를 태우거나 차를 마시거나 합니다. 대략 30분쯤 걸릴 듯.
어쨌든 이렇게 설치를 마치고 나면 최종 결과물은 `packer_virtualbox-iso_virtualbox.box` (vagrant box file)입니다.
아 이런 스크립트 디렉토리에 chef, puppet 깔고 자동으로 시스템 업데이트도 설치한다 ㅜㅜ 걍 자야겠음... ㅜㅜ

## 4. 베이그런트 박스 사용하기

생성된 파일을 베이그런트 박스로 등록하고 베이그런트파일에 설정에 넣어주고 vagrant up 해서 사용하면 됩니다~

```
vagrant box add --name osx-10.11.1 packer_virtualbox-iso_virtualbox.box

# Vagrantfile
# 리눅스처럼 게스트 에디션 기능이 완벽하게 지원되지 않아서 호스트와 게스트 파일을 싱크하려면 아래와 같이 rsync로 합니다.
config.vm.provider "virtualbox" do |vb|
  config.vm.synced_folder ".", "/vagrant", type: "rsync"
end

```

참고 문서들

* http://spin.atomicobject.com/2015/11/17/vagrant-osx/
* https://github.com/timsutton/osx-vm-templates/tree/master/scripts
* http://robb.weblaws.org/2015/10/17/os-x-el-capitan-license-in-plain-english/





