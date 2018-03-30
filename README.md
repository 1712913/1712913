# 1712913
#include <fcntl.h> //_O_U16TEXT
#include <io.h>    //_setmode()
#include <stdio.h>
#include <string.h>
struct SinhVien
{
	char mssv[10];
	wchar_t name[30], faculty[30], describe[1000], hobby[1000];
	int nienkhoa;
	int bday[3];
	char image[];
}; typedef struct SinhVien SV;
int wmain(int argc, wchar_t* argv[])
{
	FILE* fin = _wfopen(L"userinfo-c.txt", L"r, ccs=UTF-8");
	if (!fin) {
		wprintf(L"Không thể đọc file userinfo-c.txt\n");
	}
	else {
		fgetws(username, 40, fin);
		username[wcslen(username) - 1] = L'\0'; //now fgetws works fine
		fwscanf(fin, L"%lc", &gender);
		fwscanf(fin, L"%d", &age);

		wprintf(L"Họ tên: %ls\nGiới tính: %ls\nTuổi: %d\n\n", username,
			gender == L'a' ? L"Nam" : (gender == L'b' ? L"Nữ" : L"Không xác định"), age);

		fclose(fin);
	}
	wprintf(L"Chương trình kết thúc.\n");
}
