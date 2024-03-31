# 연습문제 해답
1. alt-enter눌렀을 때 화면 변경 안되게 만드세요.
```c++
  // d3dapp.cpp
  HR(dxgiFactory->CreateSwapChain(md3dDevice, &sd, &mSwapChain));
  dxgiFactory->MakeWindowAssociation(mhMainWnd, DXGI_MWA_NO_WINDOW_CHANGES);
```
2. 어댑터 수 출력하세요.
```c++
// d3dapp.cpp
UINT i = 0;
IDXGIAdapter* pAdapter;
std::vector <IDXGIAdapter*> vAdapters;
while (dxgiFactory->EnumAdapters(i, &pAdapter) != DXGI_ERROR_NOT_FOUND)
{
	vAdapters.push_back(pAdapter);
	++i;
}
std::wstring msg = L"adapter num : ";
msg += std::to_wstring(i);
MessageBox(mhMainWnd, msg.c_str(), L"Adapter num", MB_OK);
```
3. Adapter::CheckInterfaceSupport메서드를 이용해서 시스템의 어댑터들이 Direct3D 11을 지원하는지 알아내는 코드 작성
   -> 마이크로소프트에서 사용하지 말라고해서 스킵.
4. IDXGIAdapter::EnumOutputs메서드를 이용해서 기본 어탭터의 출력 대상이 몇 개인지 알아내는 코드 작성.
```c++
UINT i = 0;
IDXGIOutput* pOutput;
std::vector<IDXGIOutput*> vOutputs;
while (dxgiAdapter->EnumOutputs(i, &pOutput) != DXGI_ERROR_NOT_FOUND)
{
	vOutputs.push_back(pOutput);
	++i;
}
std::wstring msg = L"output adapter num : ";
msg += std::to_wstring(i);
MessageBox(mhMainWnd, msg.c_str(), L"Output Adapter Num", MB_OK);
```
