# EdgeWL-trace
void test01Data_init(unsigned int sand,double rate,_u8 *test01Data)
{

	u32 bit_CNT=0,temp=0;
	int i=0;

	srand(sand);
	bit_CNT=rate*16384*8;
	//bit_CNT=rate*16384;

	for(i=16384;i!=0;i--)
	{
		test01Data[i]=0;
	}
	if(rate == 1)
	{
		for(i=0;i<16384;i++)
		{
			test01Data[i]=0xff;
		}
	}
	else if(rate==0)
	{
		for(i=0;i<16384;i++)
		{
			test01Data[i]=0x00;
		}
	}
	else
	{
		for(i=0;i<bit_CNT;i++)
		{
			temp=rand()%(16384*8);
			if(((test01Data[temp/8]>>(temp%8))&0x01)==0x01)
			{
				i=i-1;
			}
			else
			{
				test01Data[temp/8]=test01Data[temp/8]|0x01<<(temp%8);
			}

		}
	}
}
