# 연습문제 해답
1. alt-enter로 화면 변경 막으시오.
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
