unit Unit1;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, Grids, DBGrids, DB, ZAbstractRODataset, ZAbstractDataset,
  ZDataset, ZAbstractConnection, ZConnection, StdCtrls, Buttons;

type
  TForm1 = class(TForm)
    ZConnection1: TZConnection;
    ZQuery1: TZQuery;
    DataSource1: TDataSource;
    DBGrid1: TDBGrid;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    Label4: TLabel;
    Label5: TLabel;
    Edit1: TEdit;
    Edit2: TEdit;
    Edit3: TEdit;
    Edit4: TEdit;
    Edit5: TEdit;
    BitBtn1: TBitBtn;
    BitBtn2: TBitBtn;
    BitBtn3: TBitBtn;
    BitBtn4: TBitBtn;
    BitBtn5: TBitBtn;
    procedure FormShow(Sender: TObject);
    procedure BitBtn1Click(Sender: TObject);
    procedure posisiawal;
    procedure editclear;
    procedure editEnable;
    procedure DBGrid1CellClick(Column: TColumn);
    procedure BitBtn5Click(Sender: TObject);
    procedure BitBtn2Click(Sender: TObject);
    procedure BitBtn3Click(Sender: TObject);
    procedure BitBtn4Click(Sender: TObject);
  private
    { Private declarations }
  public
    { Public declarations }
  end;

var
  Form1: TForm1;
  id:string;

implementation

{$R *.dfm}

procedure TForm1.FormShow(Sender: TObject);
begin
posisiawal;
end;

procedure TForm1.BitBtn1Click(Sender: TObject);
begin
editclear;

editEnable;

BitBtn1.Enabled:= False;
BitBtn2.Enabled:= True;
BitBtn3.Enabled:= False;
BitBtn4.Enabled:= False;
BitBtn5.Enabled:= True;
end;

procedure TForm1.posisiawal;
begin
editclear;
Edit1.Enabled:= False;
Edit2.Enabled:= False;
Edit3.Enabled:= False;
Edit4.Enabled:= False;
Edit5.Enabled:= False;

BitBtn1.Enabled:=True;
BitBtn2.Enabled:=False;
BitBtn3.Enabled:=False;
BitBtn4.Enabled:=False;
BitBtn5.Enabled:=False;
end;

procedure TForm1.DBGrid1CellClick(Column: TColumn);
begin
        id:= ZQuery1.Fields[0].AsString;
Edit1.Text:= ZQuery1.Fields[1].AsString;
Edit2.Text:= ZQuery1.Fields[2].AsString;
Edit3.Text:= ZQuery1.Fields[3].AsString;
Edit4.Text:= ZQuery1.Fields[4].AsString;
Edit5.Text:= ZQuery1.Fields[5].AsString;
BitBtn1.Enabled:=False;
BitBtn2.Enabled:=False;
BitBtn3.Enabled:=True;
BitBtn4.Enabled:=True;
BitBtn5.Enabled:=True;
Edit1.Enabled:=True;
Edit2.Enabled:=True;
Edit3.Enabled:=True;
Edit4.Enabled:=True;
Edit5.Enabled:=True;
end;

procedure TForm1.editclear;
begin
Edit1.Clear;
Edit2.Clear;
Edit3.Clear;
Edit4.Clear;
Edit5.Clear;
end;

procedure TForm1.editEnable;
begin
Edit1.Enabled:= True;
Edit2.Enabled:= True;
Edit3.Enabled:= True;
Edit4.Enabled:= True;
Edit5.Enabled:= True;
end;

procedure TForm1.BitBtn5Click(Sender: TObject);
begin
posisiawal;
end;

procedure TForm1.BitBtn2Click(Sender: TObject);
begin
if Edit1.Text ='' then
begin
ShowMessage('NAMA KUSTOMER TIDAK BOLEH KOSONG!');
end else
if Edit2.Text ='' then
begin
ShowMessage('No TELEPON TIDAK BOLEH KOSONG!');
end else
if Edit3.Text ='' then
begin
ShowMessage('alamat TIDAK BOLEH KOSONG!');
end else
if Edit4.Text ='' then
begin
ShowMessage('kota TIDAK BOLEH KOSONG!');
end else
if Edit5.Text ='' then
begin
ShowMessage('kodepos TIDAK BOLEH KOSONG!');
end else
begin
 ZQuery1.SQL.Clear; //simpan
ZQuery1.SQL.Add('insert into kostumer values(null,"'+Edit1.Text+'","'+Edit2.Text+'","'+Edit3.Text+'","'+Edit4.Text+'","'+Edit5.Text+'")');
ZQuery1.ExecSQL ;

ZQuery1.SQL.Clear;
ZQuery1.SQL.Add('select * from kostumer');
ZQuery1.Open;
ShowMessage('DATA BARHASIL DISIMPAN!');
posisiawal;
end;
end;

procedure TForm1.BitBtn3Click(Sender: TObject);
begin
if (Edit1.Text= '')or (Edit2.Text ='')or(Edit3.Text= '')or (Edit4.Text ='')or (Edit5.Text ='') then
begin
  ShowMessage('INPUTAN WAJIB DIISI!');
end else
if Edit1.Text = ZQuery1.Fields[1].AsString then
begin
 ShowMessage('DATA TIDAK ADA PERUBAHAN');
 posisiawal;
end else
begin
 ShowMessage('DATA BERHASIL DIUPDATE!');
ZQuery1.SQL.Clear;
ZQuery1.SQL.Add('Update kostumer set nmkostumer= "'+Edit1.Text+'",telp="'+Edit2.Text+'",alamat="'+Edit3.Text+'",kota="'+Edit4.Text+'",kodepos="'+Edit5.Text+'" where idkostumer="'+id+'"');
ZQuery1. ExecSQL;

ZQuery1.SQL.Clear;
ZQuery1.SQL.Add('select * from kostumer');
ZQuery1.Open;

posisiawal;
end;
end;

procedure TForm1.BitBtn4Click(Sender: TObject);
begin
if MessageDlg('APAKAH YAKIN MENGHAPUS DATA INI?',mtWarning,[mbYes,mbNo],0)= mryes then
begin
 ZQuery1.SQL.Clear;
ZQuery1.SQL.Add('delete from kostumer where idkostumer="'+id+'"');
ZQuery1.ExecSQL;
ZQuery1.SQL.Clear;
ZQuery1.SQL.Add('select * from kostumer');
ZQuery1.Open;
ShowMessage('DATA BERHASIL DIHAPUS');
posisiawal;
end else
begin
 ShowMessage('DATA BATAL DIHAPUS');
 posisiawal;
end
end;

end.
